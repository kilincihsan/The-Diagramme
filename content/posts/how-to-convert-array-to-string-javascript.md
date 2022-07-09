+++
title = "How to convert Array to String in JavaScript?"
date = 2022-07-09T19:55:57+03:00
draft = false
author = "İhsan Kılınç"
tags = ["javascript"]
+++
![x](/images/arr-to-str.PNG)

If you want to convert your array into a string you can use three of these methods;

1. [Using toString() Method](#convert-using-tostring)
2. [Using join() Method](#convert-using-join)
3. [Using Type Coercion](#convert-using-type-coercion)
4. [Using Type Conversion](#convert-using-type-conversion)


## Convert Using .toString()
The Array object overrides the toString() method of Object so we can use it on Arrays. This will actually call the join() method which will join each element seperated by commas. 

##### toString() syntax
{{< highlight css "linenos=false,style=tango">}}
    toString()
{{< /highlight >}}

There are **no parameters**. This won't change the original Array because it is **not destructive**. 

##### Example

```javascript
//using toString()
arr=["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m"];
console.log(arr.toString());
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
"L,o,r,e,m, ,i,p,s,u,m"
{{< /highlight >}}

Notice that, it returned each element with commas. If you don't want commas you should use join() instead because it is not possible with toString().

## Convert Using .join()
The Array object **overrides the toString() method** of Object so we can use it on Arrays. This actually "L,o,r,e,m, ,i,p,s,u,m" method which joins each element seperated by commas. 

##### join() syntax
{{< highlight css "linenos=false,style=tango">}}
    join(optional separator)
{{< /highlight >}}

**Seperator** is optional. If you use this method without parameter like this **str.join()**; 

{{< highlight css "linenos=false,style=tango">}}
    [a,b,c,d,e,f] => "a,b,c,d,e,f"
{{< /highlight >}}

Each character **joins with commas as default**.

##### Example 1

```javascript
//using toString()
arr=["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m"];
console.log(arr.join(""));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
"Lorem ipsum"
{{< /highlight >}}

In this example, we used an **empty string as seperator**. Notice that it returned **without commas** which was default.

##### Example 2

```javascript
//using join(" ")
arr=["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m"];
console.log(arr.join(" "));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
"L o r e m   i p s u m"
{{< /highlight >}}

In this example, we used **white space as seperator**. Function returned each element of this Array seperated with whitespace as String.
##### Example 3

```javascript
//using join("X")
arr=["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m"];
console.log(arr.join("X"));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
"LXoXrXeXmX XiXpXsXuXm"
{{< /highlight >}}

In this example, we used the **'X' character as seperator**. This returned each element seperated with X as String.

## Convert Using Type Coercion

Type Coercion is an automatic or implicit conversion of one data type to another. (number->string etc.) When you add string to other types JS auto converts the product to String. If you want to convert an Array to String it is handy and short.

##### Example 1

```javascript
//type coercion
arr=["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m"];
console.log(arr+"");
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
"L,o,r,e,m, ,i,p,s,u,m
{{< /highlight >}}

##### Example 2

```javascript
//type coercion
arr=["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m"];
console.log(arr+"some kind of string");
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
"L,o,r,e,m, ,i,p,s,u,msome kind of string"
{{< /highlight >}}

It can be usefull as shorter alternative to toString() but note that commas stil exists. If you want to remove commas, you can use replace functions after coercion. 

## Convert Using Type Conversion

We can use explicit type conversion when we want to change one data type to another. If you want to convert other data types to String you can use; 

##### String(object) syntax
{{< highlight css "linenos=false,style=tango">}}
    String(object)
{{< /highlight >}}

Parameter can be a number,string,array etc.

##### Example

```javascript
//type conversion
arr=["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m"];
console.log(String(arr));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
"L,o,r,e,m, ,i,p,s,u,m"
{{< /highlight >}}

## Tricks 


You can split a String and join after, if you want to replace all occurences of a character inside a String. 

![JavaScript replace trick](/images/replace-alternative.PNG)
 
**Changing "X" characters to "R"**;

```javascript
//using split and join trick to replace elements
str="AXBXCXDXEX";
console.log(str.split("X").join("R"));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
"ARBRCRDRER"
{{< /highlight >}}

## Fast Question

{{< quizdown >}}

---
primary_color: orange
secondary_color: lightgray
text_color: black
shuffle_questions: false
---

## var x = "anNoying quest ion"

---
shuffle_answers: false
---
Use split trick to remove whitespaces and change this string into **"anNoying-quest-ion"**?
> join is the opposite function of the split.

- [ ] `console.log(x.split("N").join(" "));`
- [x] `console.log(x.split(" ").join("-"));`
- [ ] `console.log(x.split(" ").join(""));`
- [ ] `console.log(x.split(" ").join("N"));`


{{< /quizdown >}}