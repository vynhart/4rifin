---
layout: post
title:  "My Impression on Go Language"
categories: golang
date:   2016-08-20 17:52:38 +0700
permalink: my-impression-on-go-programming-language/
---

![Gopher](/images/gopher.jpg)

Before I talk about my Impression to code with Go, let me acclaim that I’ve written code on ruby for a year. So I will talk about Ruby first. And hopefully I can get some comparison between these both of types programming language.

Ruby is a beautiful language, it is so expressive that you almost got no obstacle to write your thought to code. Ruby is an interpreter language, you don’t need to compile the code to run it, it will execute your code line by line without compilation to the whole code. This makes the development phase of software become faster.

Ruby too, is a dynamic typing language, means that  you don’t have to explicitly tell ruby what kind of data a variable will store, a variable will store any type of data. No matter it is a number, a string, or another object. In Ruby, everything is object, and for me, that is the one of most beautiful thing about it. You could write a loop like this:

{% highlight ruby %}
100.times do |i|
  puts "#{i} times of Hello World!"
end
{% endhighlight %}

100.times ? Oh my god what a beautiful way to tell a computer what to do.

However, on the other side. All of these luxury has cost. Because of ruby is an interpreter language, and it treat anything in code (Really, anything.) as an object, Ruby takes more memory and more resource to process your code.

One day, there comes a time when I had to write a micro service with special purpose to integrating our internal data to external third party system. My CTO told me to try Go or Lua. I chose Go.

So I take time to learn Go, read several article, and watch some video to know why should I use Go? What is good from Go?

Among the reasons, what makes me impressed is that Go have concurrency way of programming -without Thread-. More info about it, [watch here](https://www.youtube.com/watch?v=f6kdp27TYZs). Go is built in a purpose to be like C, not Java nor Ruby. It is optimized in speed because Go will compile your code directly to the native Machine code. Go is like C, but in much way better IMHO. That is, Go has Garbage Collector mechanism so as a programmer you don’t need to be bothered to free all the variables in your code, this avoid you from unnecessary bug.

Go too, has a chain mechanism. Some way to synchronize multiple Thread in another programming language. But in a different, easier, and cheaper way.

Well, I thought it’s a good programming language, the service that I would build will be fast and efficient. So I start to code.

In the first several hours, I immediately feel intimidated with this language. Again, I’ve been played with that beauty of Ruby language for full time in a year. I yelled in my mind, “What an ugly language it is”. But, again. I have to admit, this is the consequence when you get into a compiler language that will compile your code to a machine language.

I spent days to write my micro service, and man, I’m exhausted XD. It’s just so different in many ways, one of the most annoying thing I feel about Go is you have to explicitly handle EVERY SINGLE of errors that might be occurs of a statement call. Moreover, Go is not an OOP Language like ruby, so my mind suddenly have to restructure the mindset like “Oh ok, it is not an object. Well, at least I can make a method to this struct”.

But in my way to write my code in Go, I realize that along with all of the limitation of a compiler language, Go come with a really handy and flexible way to allow you express your code. Something like you can extend a method to a data type by assigning method to it, or about it’s interface mechanism, to wrap your logic to code interface, makes it so flexible to got any third party library in the same interface.

So my last statement is though it’s a bit exhausting to move from an Interpreter and beautiful Language like Ruby to a more native language like Go, I think I’m on the right track to get more knowledge and to be able to write software in Go. And for enterprise class of software, especially when it comes to SAAS (Software As A Service), performance will be a big concern. And Go has capability to be the best choice.

What about your opinion with Go? Feel free to fill in comment below.

Want to jump to learn go right now? Let’s Go.

