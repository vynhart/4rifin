---
layout: post
title:  "My CSS Self note"
categories: css
date:   2019-11-24 21:40:00 +0700
permalink: css-self-note/
---

![Gopher](https://cdn.lynda.com/course/504266/504266-636924000532723800-16x9.jpg)

This is my self note about CSS. I write it to my blog so that I can easily access anywhere as long as I got an internet connection. If in any way you find it useful, it would be my pleasure to help.

Building Block
Cascading
As it is named, style will be applied `cascaded` to an element of HTML. Which means that if there is two or more rule conflicting, say that you define background of an element <p> twice in css file, that is: blue and black. The one that will be implemented to the element is the last one found by browser, black will override blue. Thus, order is matter in css.

Specification
If there is more than one rules conflicting, the one that will be applied is the most specific one, that is in the following order of the less specific to the most:
1. Element selector. Such as: h1, p, div
2. Class selector. Such as: .send-button, .name-input
3. Id selector. Such as: #registration-form

Inheritance
Some property set in parent will be inherited to it's child like `color`, `font-family`. Some are not, like `width`. Which one is inherited and which one is not is usually common sense.

Selector
Following the specification part, css provide ways to select an element. That is:

Type, Class, and Id selector
To select certain element, class, or id.
Example: h1, .title, #name

Attribute selector
To select certain element having a particular attribute.
Example: p[title] will select element p that is having attribute `title`

Pseudo Classes and Pseudo Element
Pseudo classes is like a class that is implemented to an element at certain condition.
Example:
- button:hover will implement the defined css rule to the button when user is hovering the mouse pointer to the element.
- p:first-child will implement the defined css rule to the first child of the p

Pseudo element is similar like a pseudo class. But instead of like implementing a class to an element, it will behave like appending particular element to the html. Suppose that you want to make the first line of your paragraph to be in bold, how would you do that. Without pseudo element, you will probably enclose some of the words that you think would be the first line in <span>, give it a class, and apply CSS rule of `bold` into the class. It will work if the width of the element never change, but what if the width is changed, say, to be narrower than the words within your span would probably fill the second line too. To accomodate this needs, css provide a way to select that kind of case by providing a pseudo element.
Example:
- p::first-line will implement the defined css rule to the first line of your paragraph. If you change your browser width, it will automatically adjust the words that needs to be styled to meet the needs.
- p::before will implement the defined css rule to 'before' of the element. Say that you want every paragraph started with a dollar symbol, than you would defined the css rule like:
p::before { content: "$" }
- p::after acts similar like p::before, but it will apply in the after.

