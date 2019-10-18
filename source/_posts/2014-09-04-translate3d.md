---
title: Unable to stop CSS3 transition of transform by translate3d
date: 2014-09-04 21:42:37
categories:
- 代码
tags:
- css
---


``` javascript
// for start animation
$("#content")
    .css("-webkit-transition", "all 100s");
    .css("-webkit-transform", "translate(0, -900px)");

// for stop animation
$("#content")
    .css("-webkit-transition", "none");
```

In desktop Chrome and Safari is good, but in the default browser on Android 4.1.x (SGSII, Galaxy Nexus, etc) this approach does not work - transition does not stop. Additionally, I note that the situation is only a relatively translate3d: with translate and position CSS props (e.g. "top", "left") it works.

The transition implementation on Android 4 seems to be buggy in cases where a transitioning hardware-rendered layer is canceled by adjusting the webkitTransitionDuration to 0 (and setting webkitTransition to 'none' or '' often implies this). This can be circumvented by using a transition duration of .001ms or similar, although this very likely still draws multiple frames.

A more practical work-around on at least certain devices is to use a negative value for the webkitTransitionDelay, forcing a new transition to take effect, but choosing this value such that the transition starts directly in its finished state.

Like so:

``` javascript
e.style.webkitTransition = '-webkit-transform linear 10s';
e.style.webkitTransform = 'translate3d(100px,100px,0)';
```

now cancel 10s-long transition in 1s and reset transformation

``` javascript
setTimeout(function() {
    e.style.webkitTransitionDelay = '-10s'
    e.style.webkitTransform = 'translate3d(0,0,0)';
}, 1000);
```
