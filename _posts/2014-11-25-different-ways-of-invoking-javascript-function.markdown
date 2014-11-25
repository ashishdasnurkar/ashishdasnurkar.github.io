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

Let's take a look at each of these methods in detail with sample code

#### 1. Invoking functions as functions


