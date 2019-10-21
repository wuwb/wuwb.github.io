---
title: AnimationEvent
date: 2014-08-11 19:30:00
updated: 2014-08-11 19:52:00
categories:
- 代码
tags:
- javascript
- classes
------

{% blockquote %}
**这是一个试验性的技术**
因为这项技术的规范还没稳定下来，在不同浏览器中使用前请先检查兼容表查看对应的前缀。另外需要注意的是试验性技术的语法和行为随着规范的变化在未来版本的浏览器中可能会发生改。
{% endblockquote %}

### Summary

AnimationEvent 接口提供与 animations 相关的信息。

### Properties

还从父类 Event 中继承属性。

- AnimationEvent.animationName **Read only**
  - Is a DOMString containing the value of the animation-name CSS property associated with the transition.

- AnimationEvent.elapsedTime Read only
Is a float giving the amount of time the animation has been running, in seconds, when this event fired, excluding any time the animation was paused. For an "animationstart" event, elapsedTime is 0.0 unless there was a negative value for animation-delay, in which case the event will be fired with elapsedTime containing  (-1 * delay).

- AnimationEvent.pseudoElement Read only
Is a DOMString, starting with '::', containing the name of the pseudo-element the animation runs on. If the animation doesn't run on a pseudo-element but on the element, an empty string: ''.

### Constructor

- AnimationEvent()
  - 根据参数创建一个 AnimationEvent 事件。

### Methods

还从父类 Event 中继承方法。

- AnimationEvent.initAnimationEvent()
  - Initializes a AnimationEvent created using the deprecated Document.createEvent("AnimationEvent") method.

### Reference

http://developer.mozilla.org/en-US/docs/Web/API/AnimationEvent.html
