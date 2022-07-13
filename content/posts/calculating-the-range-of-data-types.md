+++
title = "How to calculate range of data types"
date = 2022-07-12T23:56:28+03:00
draft = false
author = "İhsan Kılınç"
tags = ["Assembly"]
+++

These are built-in and predefined data types can be used for declaring variables;

* Integer
* Float
* Double
* Character
* Boolean
* Wide Character
* Void

And they have modifiers like;
- Short
- Long
- Signed
- Unsigned

Each of them will allocate a memory space and have a range of values they can hold related to this space. For example, char requires 1 byte, int requires 4 byte, long and double requires 8 byte. And all have different ranges related to that space. It can change by size and generalization for each programming language but it is common or similar for most of the programming languages.

## Range Calculation

Default values can be seperated as signed and unsigned. 
- Unsigned values can not be negative (range of unsigned char:. 0,255) 
- Signed values can be negative or positive (range of signed char: -128,127)

And note that, it is all **signed by default**.

You can calculate the range with these formulas;

#### For Signed:

### ```Minimum:0 Maximum:2^n-1```

#### For Unsigned:

### ``` Minimum:-2^(n-1) Maximum:2^(n-1)-1 ```

#### Signed Example:
* For example lets define a char;
* char c=0;
* We know that char requires 1 byte(8 bit)
* We know it will be signed by default.
* Formula for signed;
* **minimum -2^(n-1)** = -2^7 = -128
* **maximum  2^(n-1)-1** = 2^7-1 = 127

#### Unsigned Example:
* Lets define an unsigned long to understand it better;
* unsigned long x=0;
* We know that long requires 8 byte(64 bit)
* We know it is unsigned we added it to beginning of identifier.
* Formula for unsigned;
* **minimum was 0** = 0
* **maximum was (2^n)-1** = 2^64-1 = 18446744073709551615

So the **character we defined** can take values between **0 and 18446744073709551615**. 

## Quiz

{{< quizdown >}}

---
primary_color: orange
secondary_color: lightgray
text_color: black
shuffle_questions: false
---

## ``` unsigned char c = 0;```

---
shuffle_answers: false
---

What is the range of this char?

> 1 byte

- [ ] -127 to 127 
- [ ] 0 to 65,535
- [ ] -32768 to 32767
- [x] 0 to 255

## ``` short z;```

What is the range of this short?

> 2 byte

- [ ] -127 to 127 
- [ ] 0 to 65,535
- [X] -32768 to 32767
- [ ] 0 to 255
{{< /quizdown >}}