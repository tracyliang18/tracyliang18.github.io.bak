---
layout: post
title: python attributes and methods
---

一直以来用python都是边查边用，而且都是用在日常的小脚本而已，用过写过一个计算机网络的课程设计，感觉蛮爽，但一直都是感觉处于这种不熟练、不精通的感觉。

最近在看python实现的design pattern代码，上述的缺点马上无所遁形。上一个visitor模式代码：

{% highlight python linenos %}
ass Node(object): pass
class A(Node): pass
class B(Node): pass
class C(A,B): pass

class Visitor(object):
    def visit(self, node, *args, **kwargs):
        meth = None
        for cls in node.__class__.__mro__:
            meth_name = 'visit_'+cls.__name__
            meth = getattr(self, meth_name, None)
            if meth:
                break

        if not meth:
            meth = self.generic_visit
        return meth(node, *args, **kwargs)

    def generic_visit(self, node, *args, **kwargs):
        print('generic_visit '+node.__class__.__name__)

    def visit_B(self, node, *args, **kwargs):
        print('visit_B '+node.__class__.__name__)
        



a = A()
b = B()
c = C()
visitor = Visitor()
visitor.visit(a)
visitor.visit(b)
visitor.visit(c)
{% endhighlight %}

vistor 模式，举个好理解的例子：
习总要到不同国家访问，所用的外交策略肯定是不一样的，在美国面前就是小熊维尼，在日本面前就是绿巨人。不同国家有相应的一套东西迎接中国来访。

从程序设计的角度去理解，习总这个对象，拥有访问不同国家的方法，而各国有一个名为accpet的方法去接待习总，当然具体实现肯定不一样啦。把各个国家对象合并到一个对象集，把习总这个对象传到这个对象集里，即实现visitor模式。

其实上述的东西很好理解，（设计模式的东西都很好理解，只是在恰当的时机恰好地选择运用恰当的模式，很难），但我看到诸如node.__class__.__mro__，cls.__name__这样的设计到python自带属性和方法，就感觉自己真的一点都不懂python。。

( python attributes and methods)[http://www.cafepy.com/article/python_attributes_and_methods/python_attributes_and_methods.html]

看上去是个不错的教程，先看看。。稍后更新
