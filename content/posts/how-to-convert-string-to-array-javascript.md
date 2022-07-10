+++
title = "How to convert String to Array in JavaScript?"
date = 2022-07-04T20:26:26+03:00
draft = false
author = "İhsan Kılınç"
tags = ["JavaScript"]
+++

![x](/images/js/str-to-arr.PNG)

If you want to convert your string into an array without writing complex code you have 4 options;

- Using String.split() 
- Using Spread Operator [...String]
- Using Array.from(String)
- Usign Object.assign([],string)


## 1. Using split() Method
This is the most popular method for **converting a string to an array** and is also used for a few other javascript tricks like replacing all of the occurrences for given character. It is not a destructive method which means it doesn't change the original value, just returns another copy of it.

###### Split syntax
{{< highlight css "linenos=false,style=tango">}}
    str.split(seperator,limit)
{{< /highlight >}}

**Seperator** and **Limit** are optional parameters. 

If you leave **seperator undefined(str.split())** it will return **original string as array**.

{{< highlight css "linenos=false,style=tango">}}
    "abcdefghi" => ["abcdefghi"]
{{< /highlight >}}
###### Example 1

```javascript
//using split("")
str="Lorem ipsum dolor sit amet"
console.log(str.split(""));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m", " ", "d", "o", "l", "o", "r", " ", "s", "i", "t", " ", "a", "m", "e", "t"]
{{< /highlight >}}

In this example, we used an **empty string as seperator**. This returns every character in given string as array.

###### Example 2

```javascript
//using split(" ")
str="Lorem ipsum dolor sit amet"
console.log(str.split(" "));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
["Lorem", "ipsum", "dolor", "sit", "amet"]
{{< /highlight >}}

In this example, we used a **whitespace as seperator**. This will return the **given string seperated by whitespace as array**.

###### Example 3

```javascript
//using split with seperator string
str="Lorem ipsum dolor sit amet"
console.log(str.split("s"));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
"Lorem ip", "um dolor ", "it amet"]
{{< /highlight >}}

In this example, we used the **"s" character as seperator**. This returns every character in the **given string seperated by 's' as an array**. Notice that, 's' not included in result.

## 2. Using [...String]

It is an **operator** and **not destructive** which means it is not going to change the original string just returns a copy of it.

###### Example 1

```javascript
//using split method
str="Lorem ipsum dolor sit amet"
console.log([...str]);
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m", " ", "d", "o", "l", "o", "r", " ", "s", "i", "t", " ", "a", "m", "e", "t"]
{{< /highlight >}}

This returns every character in given string as array just like str.split().

## 3. Using Object.assign()

Originally used for **cloning an object with its properties**, but we are going to use it for converting a string into an array for each character. It is not destructive, it is a cloning process.

###### Example

```javascript
//using object assign
str="Lorem ipsum dolor sit amet"
console.log(Object.assign([],str));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m", " ", "d", "o", "l", "o", "r", " ", "s", "i", "t", " ", "a", "m", "e", "t"]
{{< /highlight >}}

##  4. Using Array.from()

Originally used for **cloning an array**. It is **not destructive**, result will be copy of an array(array-like).

###### Example

```javascript
//using array from
str="Lorem ipsum dolor sit amet"
console.log(Array.from(str));
```
###### Output
{{< highlight css "linenos=false,style=tango">}}
["L", "o", "r", "e", "m", " ", "i", "p", "s", "u", "m", " ", "d", "o", "l", "o", "r", " ", "s", "i", "t", " ", "a", "m", "e", "t"]
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