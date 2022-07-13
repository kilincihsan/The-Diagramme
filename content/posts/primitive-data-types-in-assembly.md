+++
title = "Primitive Data Types in Assembly"
date = 2022-07-13T18:33:18+03:00
draft = false
author = "İhsan Kılınç"
tags = ["Assembly"]
+++

**Each type of variables** will allocate a **memory space**. For example, char requires 1 byte, int requires 4 bytes, and long and double require 8 bytes. And **all have different ranges related to that size**. It can change by size and generalization for each programming language but it is the same or similar for most programming languages. Let's analyze variables for C++;

* Integer
* Float
* Double
* Character
* Boolean
* Wide Character
* Void

For example; when you define one of those, **compiler generates a size directive** and tells **how much does it gonna cost** to your memory. Let's look at size directives in more detail.

##  Size Directives

Size directives tell the intended size of the data at given memory address. 
* mov BYTE PTR [ebx], 2	
* this will move 1 byte represantation of 2
* mov WORD PTR [ebx], 2	
* this will move 2 byte represantation of 2
* mov DWORD PTR [ebx], 2
* this will move 4 byte represantation of 2 


{{<table "table table-striped table-bordered">}}

| Scalar type             	| C data type                 	| Storage size (in bytes) 	| Recommended alignment 	|
|-------------------------	|-----------------------------	|-------------------------	|-----------------------	|
| INT8                    	| char                        	| 1                       	| Byte                  	|
| UINT8                   	| unsigned char               	| 1                       	| Byte                  	|
| INT16                   	| short                       	| 2                       	| Word                  	|
| UINT16                  	| unsigned short              	| 2                       	| Word                  	|
| INT32                   	| int, long                   	| 4                       	| Doubleword            	|
| UINT32                  	| unsigned int, unsigned long 	| 4                       	| Doubleword            	|
| INT64                   	| __int64                     	| 8                       	| Quadword              	|
| UINT64                  	| unsigned __int64            	| 8                       	| Quadword              	|
| FP32 (single precision) 	| float                       	| 4                       	| Doubleword            	|
| FP64 (double precision) 	| double                      	| 8                       	| Quadword              	|
| POINTER                 	| *                           	| 8                       	| Quadword              	|
| __m64                   	| struct __m64                	| 8                       	| Quadword              	|
| __m128                  	| struct __m128               	| 16                      	| Octaword              	|

{{</table>}}

### Example

**In this example**; I used **Visual Studio Disassembly Tool** to share with you what happens when you define primitive variables. You can do this yourself while debugging; press the hotkey **CTRL+ALT+D** or **right click > go to disassembly**.

{{< highlight cpp "linenos=true,style=dracula">}}
#include <iostream>
#include <conio.h>

using namespace std;

int main() {
    //requires 4 bytes
    int a = 3; 
    //requires 4 bytes
    float b = 3.9;
    //requires 8 bytes
    double c = 4.11;
    //requires 1 bytes
    char d = 'D';
    //requires 1 bytes
    bool e = true;
    //it will take 1 byte per character + 1 for zero
    string f = "Hello world!";
}

{{< /highlight >}}


### Output

{{< highlight cpp "linenos=false,style=tango">}}
    int a = 3; 
00007FF7BD75479D  mov         dword ptr [a],3  
    float b = 3.9;
00007FF7BD7547A4  movss       xmm0,dword ptr [__real@4079999a (07FF7BD75E1D4h)]  
00007FF7BD7547AC  movss       dword ptr [b],xmm0  
    double c = 4.11;
00007FF7BD7547B1  movsd       xmm0,mmword ptr [__real@401070a3d70a3d71 (07FF7BD75DC10h)]  
00007FF7BD7547B9  movsd       mmword ptr [c],xmm0  
    char d = 'D';
00007FF7BD7547BE  mov         byte ptr [d],44h  
    bool e = true;
00007FF7BD7547C2  mov         byte ptr [e],1  
    string f = "Hello world!";
00007FF7BD7547C9  lea         rdx,[string "Hello world!" (07FF7BD75E1E0h)]  
00007FF7BD7547D0  lea         rcx,[f]  
00007FF7BD7547D7  call        std::basic_string<char,std::char_traits<char>,std::allocator<char> >::basic_string<char,std::char_traits<char>,std::allocator<char> > (07FF7BD751249h) 
{{< /highlight >}}

### Summary

Looking at the assembler version, you can see all of them have a size directive due to the corresponding type. For our example these are;

*int -> dword
*float -> dword
*double -> mmword
*char -> byte
*bool -> byte

**mmword** stands for multimedia word,**dword** is for double word and they are in sizes like 1-2-4-8 bytes. Checking the code again string definition did not use any of these because size of it is 1 byte for each character + 1 byte for the terminator.

You might also want to check this and learn about [Calculating Range of Data Types](https://thediagramme.com/how-to-calculate-range-of-data-types).

Feel free to contact me about the subject info@thediagramme.com

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

What is the equivelant of this char?

> You can check the table.

- [X] byte
- [ ] word
- [ ] dword
- [ ] qword

## ``` short z;```

What is the equivelant of this short?

> You can check the table.

- [ ] byte
- [X] word
- [ ] dword
- [ ] qword
{{< /quizdown >}}

{{ template "_internal/disqus.html" . }}