WordPress优化小技巧，禁用Jquery Migrate文件

WordPress优化小技巧，禁用Jquery Migrate文件
想要优化网站打开速度，其中一点 就是减少网站资源请求数量，而我们使用WordPress安装的网站，默认会引用一个jquery-migrate.min.js的JavaScript库，通常情况，我们都可以禁止引用这个Jquery Migrate文件以减少一次资源请求。

下面一起来看看怎么禁用jquery-migrate.min.js吧。

jquery-migrate.min.js介绍
jQuery Migrate是一个JavaScript库，它可以实现1.9版本以下的jQuery代码兼容，WordPress 3.6开始就默认包含在了网站加载资源里面。

绝大多数新版本的插件或者主题代码都不需要jquery-migrate.min.js，所以如果你确保你网站没有那些年龄很久并且需要这个js文件的话，就可以禁用它以避免在网站前台加载。

禁用jquery-migrate.min.js的方法
可以使用插件禁用，也可以使用代码禁用，考虑到代码禁用的方法很简单，所以就不推荐使用插件方式了。但是，如果你不会修改代码，那么可以安装一个修改代码的插件帮你，因为会经常用到它的功能。

安全添加代码到functions.php文件的方法：Code Snippets

具体的禁用代码如下:

//移除jQuery Migrate脚本
//https://blog.naibabiji.com/wang-zhan-zi-xun/jin-yong-jquery-migrate-min-js.html
function dequeue_jquery_migrate( $scripts ) {
    if ( ! is_admin() && ! empty( $scripts->registered['jquery'] ) ) {
        $scripts->registered['jquery']->deps = array_diff(
            $scripts->registered['jquery']->deps,
            [ 'jquery-migrate' ]
        );
    }
}
add_action( 'wp_default_scripts', 'dequeue_jquery_migrate' );
上面的代码添加到主题文件的functions.php里面，可以防止将jQuery Migrate脚本加载到前端，同时保持jQuery脚本本身完整无缺。它仍在管理员中加载，不会破坏任何内容。

更多和WordPress优化的相关的文章：

很好用的WordPress优化速度插件推荐：Hummingbird
想优化WordPress的打开速度？让gtmetrix来帮忙
网站速度跟什么有关_影响网站速度慢的8个方面
