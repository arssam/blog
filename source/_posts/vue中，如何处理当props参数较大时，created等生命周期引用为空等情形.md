---
title: vue中，如何处理当props参数较大时，created等生命周期引用为空等情形
date: 2019-01-15 10:44:51
tags: 'vue'
---

当子组件中接受的props是ajax异步获取时，想要在生命周期created，mounted等钩子，data选项获取ajax后的参数，可能获取不到

解决方案： 在watch中处理参数即可

此类问题再取后台参数渲染组件中比较常见