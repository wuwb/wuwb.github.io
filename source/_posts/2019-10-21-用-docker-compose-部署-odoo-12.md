---
title: 用 docker compose 部署 odoo 12
date: 2019-10-21 21:55:44
timestamp: 2019-10-21 21:55:44
updated:
tags: odoo
---

先是一个合并两个服务的 docker compose 编排方式。

```yaml
version: '3.1'

services:
  odoo:
    image: odoo:12.0
    container_name: odoo
    depend_on: postgres
    ports:
      - "8069:8069"
    networks:
      - odoo
    environment:
      - HOST=postgres
      - PORT=5432
      - USER=odoo
      - PASSWORD=odoo
    volumes:
      - /share/Container/data/odoo/data:/var/lib/odoo
      - /share/Container/data/odoo/config:/etc/odoo
      - /share/Container/data/odoo/addons:/mnt/extra-addons

  postgres:
    image: postgres:10
    container_name: postgres
    restart: always
    ports:
      - "5432:5432"
    networks:
      - odoo
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_USER=odoo
      - PGDATA=/var/lib/postgresql/data/pgdata
    volumes:
      - /share/Container/data/postgres/data:/var/lib/postgresql/data/pgdata

networks:
    odoo:
        external: true
```

有些人可能想把 postgres 分出来，给其他服务共同使用。那要的话，可以把 postgres 拿出来单独放一个 docker-compose 配置中，然后 odoo 的 compose 文件中通过 link 将两个容器连接起来，连接起来后两个容器的 hosts 中会自动注入各自容器 ip 和 别名，比如：

```
172.17.2.186  postgres
172.17.2.186  odoo
```

同样的，odoo 的环境变量配置中设置 HOST=postgres 就可以。
