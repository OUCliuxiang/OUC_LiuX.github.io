---
layout:     post
title:      Series Articles of Java Learning  -- 04
subtitle:   Java学习实录02 -- 总结一些函数方法的用法
date:       2021-01-31
author:     OUC_LiuX
header-img: img/wallpic02.jpg
catalog: true
tags:
    - 学习
    - Java
---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>  


## List 和 ArrayList   
[Java项目实录02](https://www.ouc-liux.cn/2021/01/30/Series-Record-of-Java-Learning-02/)开头有这么一行代码：    
```java   
List<NameValuePair> params = new ArrayList<NameValuePair>();
```   
试图建立一个ArrayList（泛型）对象，再将之指向到List（泛型）。对该语句的正确解释是：   

List是一个接口，而ArrayList是List接口的一个实现类。   
ArrayList类是继承AbstractList抽象类和实现List接口的一个实现类。   
因此，List接口不能被构造，也就是我们说的不能创建实例对象，但是我们可以为List接口创建一个指向自己的对象引用，而ArrayList实现类的实例对象就在这充当了这个指向List接口的对象引用。  

我们进行一组对比：   
```java   
List list = new ArrayList();        # 1
List list = new List();             # 2
ArrayList alist = new ArrayList();  # 3
```    

上面三行代码中，**1** 是可行的用法，这个语句创建了一个ArrayList实现类的对象后把它上溯到了List接口。此时它就是一个List对象了，有些ArrayList类具有的，但是List接口没有的属性和方法，它就不能再用了。   
而**3** 创建的实现类ArrayList的对象则保留了ArrayList的所有属性和方法。   
**2** 是错误的写法，由于接口类List无法具体实现为对象，该句无法执行。    