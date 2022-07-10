+++
title = "How to Setup Assembly in Visual Studio"
date = 2022-07-10T02:24:05+03:00
draft = false
author = "İhsan Kılınç"
tags = ["Assembly"]
+++

![Microsoft Macro Assembler](/images/asm/masm.jpg)

**If you want to use Assembly on Visual Studio follow the steps below;**

1. Create new project (Ctrl+Shift+N) > Empty C++ Project
2. Right click project > Build Dependencies > Build Customizations > Check .masm

![Check .masm](/images/asm/s1.PNG)

3. Right click project > Add > New Item > create main.cpp (name it whatever you want)
4. Right click project > Add > New Item > create test.asm (it must be named something different from cpp)
5. Right click .asm file > Properties > Item Type > Microsoft Macro Assembler

![Item type - Microsoft Macro Assembler](/images/asm/s2.PNG)

6. Copy the code below and start debug.

## main.cpp
Copy this code to your cpp file;

{{< highlight cpp "linenos=true,style=tango">}}
    #include <iostream>

    using namespace std;
    extern "C" int getData();

    int main()
    {
        cout << "Returns::" << getData() << endl;
        return 0;

    }

{{< /highlight >}}

## test.asm
Copy this code to your asm file;

{{< highlight cpp "linenos=true,style=tango">}}
.data
.code
getData proc
;x=10
mov rax,10 
;x++
inc ax 
;x*=10
imul ax,10 
ret
getData endp
end

{{< /highlight >}}

## How to Debug?
You want to see **registers** and **memory** and everything if ur dealing with Assembly. Thats how you gonna do it;

1. Create a breakpoint in your asm code. (click left side of line nos)
2. Start debug.(F5 default)
3. From the upper menu > Debug > Windows > check register and memory
>These windows only appear when debug happen. They will appear automatically after that so you don't need to reopen them every time. Use F11 to iterate through.

## Summary

We are using MASM(Microsoft Macro Assembler) and C++ both together to work on Assembly. The reason behind is; sometimes you simply don't want to deal with Assembly while sending parameters, showing result, using a library, generate some random number etc. That's where C++ come handy. Probably, you will not write any C++ code but it will be helpfull for simple tasks where you don't want to deal with interrupts.  

As an alternative you can use Visual Studio Code with plugins like dosbox, gnu etc., but it is easier to use and debug if you choose Visual Studio. And most of the alternative setups consume your energy without even writing any code.

If you don't know where to go after this. You can check the Assembly tag and find threads about tutorials and examples. Good luck! 
