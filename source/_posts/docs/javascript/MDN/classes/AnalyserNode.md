---
title: AnalyserNode
date: 2014-08-11 19:30:00
updated: 2014-08-11 19:52:00
comments: true
categories:
- 代码
tags:
- javascript
- classes
------


{% blockquote %}
This article is in need of a technical review
{% endblockquote %}

{% blockquote %}
**草稿**
未完成
{% endblockquote %}

{% blockquote %}
**这是一个试验性的技术**
因为这项技术的规范还没稳定下来，在不同浏览器中使用前请先检查兼容表查看对应的前缀。另外需要注意的是试验性技术的语法和行为随着规范的变化在未来版本的浏览器中可能会发生改。
{% endblockquote %}

AnalyserNode 接口代表一个可以提供实时频率和时域分析信息的节点。是一个 AudioNode，将音频流无改变的从输入源导向输出源。这
个节点在 输出源没有连接上的时候也能够工作。

![图]
{% blockquote %}
输入源个数：1
输出源个数：1（但是可以留空表示未连接）
信道数量模式：“explicit”
信道数量：1
信道阻断器：“speakers”
{% endblockquote %}


Properties
----------
从父类 AudioNode 继承属性

- AnalyserNode.fftSize
  - 一个无符号长型的值，用来表式傅立叶变化的大小以用来确定频域。它必须是介于32和2048之间的2的幕数，非零。如果不是2的幕，或者超出了规定的范围，会抛出 INDEX_SIZE_ERR 的错误。

- AnalyserNode.frequencyBinCount **只读**
  - 无符号长整型。 containing half the FFT size.

- AnalyserNode.minDecibels
  - Is a double value representing the minimum power value in the scaling range for the FFT analysis data for conversion to unsigned byte values. If a value greater than AnalyserNode.maxDecibels is set, an INDEX_SIZE_ERR exception is thrown. 默认值是 -100.

- AnalyserNode.maxDecibels
  - Is a double value representing the maximumum power value in the scaling range for the FFT analysis data for conversion to unsigned byte values. If a value smaller than AnalyserNode.minDecibels is set, an INDEX_SIZE_ERR exception is thrown. 默认值是 -30.

- AnalyserNode.smoothingTimeConstant
  - Is a double value representing the averaging constant with the last analysis frame. It must be between 0 and 1, included and defaults to 0.8 (and 0 meaning no time averaging). If outside this range, an INDEX_SIZE_ERR exception is thrown

Methods
----------
从父类 AudioNode 继承方法

Analyser.getFloatFrequencyData()
Copies the current frequency data into the array, the passed floating-point array. If the array has fewer elements than the frequencyBinCount, excess elements are dropped. If it has more elements than needed, excess elements are ignored.

Analyser.getByteFrequencyData()
Copies the current frequency data into the array, the passed unsigned byte array. If the array has fewer elements than the frequencyBinCount, excess elements are dropped. If it has more elements than needed, excess elements are ignored.

Analyser.getByteTimeDomainData()
Copies the current waveform, or time-domain, data into the array, the passed unsigned byte array. If the array has fewer elements than the fftSize, excess elements are dropped. If it has more elements than needed, excess elements are ignored.


Reference
---------
http://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode

> 2014-08-19 Wenbin
