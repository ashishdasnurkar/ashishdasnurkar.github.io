---
layout: post
title: "Different ways of invoking JavaScript functions"
date: 2014-11-25 00:01
comments: true
categories: functions, jsfoundations, jsbasics
published: false
---

In JavaScript the way a function is invoked has a significant impact on how the code within it executes, especially regarding <code>this</code> parameter.

If you have followed couple of my earlier posts I have demonstrated two ways of invoking functions already and they are
#### 1. Invoking functions as, surprise, functions
#### 2. Invoking functions as object methods

Now in addition to these two there are two more ways of invocations
#### 3. Invoking functions as constructors
#### 4. Invoking functions using <code>apply()</code> and <code>call()</code> methods

Before I dig into details of each type of function invocation, I must explain two important concepts two implicit parameters <code>argumetns</code> and <code>this</code> that are passed to every invoked function.

### <code>arguments</code> *collection*
Whenver a function is invoked in any of the four ways mentioned above, it can also be supplied with list of arguments which in turn are assigned to the parameters in the same order as defined in function declaration.

When the number of arguments match number of parameters then first argument is assigned to the first parameter, second argument is assigned to the second parameter and so on.

When the number of arguments are less than number of parameters then the parameters that have no corresponding arguments are set to undefined.

When the number of arguments are more than number of parameters then these extra aruments are simply not assigned to any parameters. Important thing to note though is that there is a way to access these extra arguments via implicit parameter called <code>arguments</code>

This implicit <code>arguments</code> parameter is quite deceptive. As in it acts like an array but it isn't really an array. It has <code>length</code> property, its elements can be accessed using array notation and it can also be iterated just like an array can be. But it doesn't have all array methods available on it.

### <code>this</code> parameter

This notion of <code>this</code> implicit reeference comes from object-oriented languages where methods are usually invoked in the context of an object and <code>this</code> generally points to this *function context* object. In JavaScript also if you invoke a function as an object's method then its *function context* is the object and it means <code>this</code> implicit references to the object. However invoking function is just one of the four ways of invoking a function. 

Let's take a look at each of these four ways of invoking functions and what effect they have on the implicit <code>this</code> parameter they have in detail with sample codes

#### 1. Invoking functions as functions
A function can be invoked simply using the () operator on any expression that resolves to a function reference.

{% highlight javascript %}
function a() {
	console.log(this); // prints [object Window]
}
a(); 
{% endhighlight %}

When function is invoked in this manner the function context is Window i.e. the global context. This is true even when a function is deeply nested within other functions.

{% highlight javascript %}
function a() {
    function b() {
       function c() {
          console.log(this); // prints [object Window]
       }
       c();
    }
    b();
}
a(); 
{% endhighlight %}

In above code, for function <code>c</code> function context is still <code>Window</code>

#### 2. Invoking functions as object methods
As we saw in earlier post
