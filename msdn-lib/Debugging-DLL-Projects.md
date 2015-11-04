
[Source](https://msdn.microsoft.com/en-us/library/ms164704.aspx "Permalink to Debugging DLL Projects")

# Debugging DLL Projects

The following templates create DLLs:

* (C++, C#, and Visual Basic) Class Library
* (C++, C#, and Visual Basic): Windows Forms Control Library

Debugging a Windows Control Library is similar to debugging a Class Library project. In most cases, you will call the Windows control from another project. When you debug the calling project, you can step into the code of your Windows control, set breakpoints, and perform other debugging operations. For more information, see [Windows Forms Controls][2].

* (C# and Visual Basic): Web Control Library

For more information, see [Web Control Library (Managed Code)][3].

* (C++): MFC ActiveX Control and MFC Smart Device ActiveX Control

ActiveX controls are controls that can be downloaded over the Internet onto a client computer, and displayed and activated on Web pages.

Debugging ActiveX controls is similar to debugging other kinds of controls because they cannot be run as stand-alone, but must be embedded in an HTML Web page. For more information, see [How to: Debug an ActiveX Control][4].

* (C++): MFC Smart Device DLL

For more information, see [MFC Debugging Techniques][5].

This section also contains information about the following topics:

* [How to: Debug from a DLL Project][15]
* [How to: Debug in Mixed Mode][16]

This topic contains the following sections, which provide considerations about how to prepare to debug class libraries:

* [Building a Debug Version][17]
* [Mixed-Mode Debugging][18]
* [Changing Default Configurations][19]
* [Ways to Debug the DLL][20]
* [The Calling Application][21]
* [Controls on a Web Page][22]
* [The Immediate Window][23]
 
##Building a Debug Version
No matter how you start debugging, make sure that you build the Debug version of the DLL first and make sure that the Debug version is in the location where the application expects to find it. This may seem obvious, but if you forget this step, the application might find a different version of the DLL and load it. The program will then continue to run, while you wonder why your breakpoint was never hit. When you are debugging, you can verify which DLLs your program has loaded by opening the debugger's **Modules** window. The **Modules** window lists each DLL or EXE loaded in the process you are debugging. For more information, see [How to: Use the Modules Window][6].

For the debugger to attach to code written in C++, the code must emit **DebuggableAttribute**. You can add this to your code automatically by linking with the [/ASSEMBLYDEBUG][7] linker option.

##Mixed-Mode Debugging
The calling application that calls your DLL can be written in managed code or native code. If your managed DLL is called by native code and you want to debug both, managed and native debuggers must both be enabled. You can select this in the **<project>****Property Pages** dialog box or window. How you do this depends on whether you start debugging from the DLL project or the calling application project. For more information, see [How to: Debug in Mixed Mode][8].

##Changing Default Configurations
When you create a console application project with the project template, Visual Studio automatically creates required settings for the Debug and Release configurations. If necessary, you can change those settings. For more information, see [Project Settings for a C++ Debug Configuration][11], [Project Settings for C# Debug Configurations][12], [Project Settings for a Visual Basic Debug Configuration][13], and [How to: Set Debug and Release Configurations][14].

##Ways to Debug the DLL
Each of the projects in this section creates a DLL. You cannot run a DLL directly; it must be called by an application, usually an EXE. For more information, see [Creating and Managing Visual C++ Projects][9]. The calling application might fit any one of the following criteria:
* An application built in another project in the same Visual Studio solution that contains the class library.
* An existing application already deployed on a test or production computer.
* Located on the Web and accessed through a URL.
* A Web application that contains a Web page which embeds the DLL.

###Debugging the Calling Application

To debug a DLL, start by debugging the calling application, typically either an EXE or a Web application. There are several ways to debug it.

* If you have a project for the calling application, you can open that project and start execution from the **Debug** menu. For more information, see .b0fe0ce5-900e-421f-a4c6-aa44ddae453c
* If the calling application is an existing program already deployed on a test or production computer and is already running you can attach to it. Use this method if the DLL is a control hosted by Internet Explorer, or a control on a Web page. For more information, see .636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4
* You can debug it from the DLL project. For more information, see [How to: Debug from a DLL Project][10].
* You can debug it from the Visual Studio&nbsp;**Immediate** window. In this case, the **Immediate** window plays the role of the application.

Before you start debugging the calling application, you will usually want to set a breakpoint in the class library. For more information, see . When the breakpoint is hit, you can step through the code, observing the action at each line, until you isolate the problem. For more information, see .fe4eedc1-71aa-4928-962f-0912c334d5838791dac9-64d1-4bb9-b59e-8d59af1833f9

### Controls on a Web Page

To debug a Web page control, create an ASP.NET page that embeds it if such a page does not already exist. You then place breakpoints in the Web page code as well as the control code. You then invoke the Web page from Visual Studio.

Before you start debugging the calling application, you will usually want to set a breakpoint in the DLL. When the breakpoint is hit, you can step through the code, observing the action at each line, until you isolate the problem. For more information, see .FE4EEDC1-71AA-4928-962F-0912C334D583

### The Immediate Window

You can evaluate functions or methods in the DLL without having a calling application. You do design-time debugging and you use the **Immediate** window. To debug in this manner, do the follow these steps while the DLL project is open:

1. Open the Debugger **Immediate** window.

2. To test a method named Test in class Class1, instantiate an object of type Class1 by typing the following C# code in the Immediate window. This managed code works for Visual Basic and C++, with appropriate syntax changes:

        Class1 obj = new Class1();
In C#, all names must be fully qualified. In addition, any methods or variables must be in the current scope and context of the debugging session.
3. Assuming that Test takes one int parameter, evaluate Test using the **Immediate** window: 
```
?obj.Test(10)
```
The result will be printed in the **Immediate** window.
4. You can continue to debug Test by placing a breakpoint inside it and then evaluating the function again:
```
?obj.Test(10);
```
The breakpoint will be hit and you will be able to step through Test. After execution has left Test, the Debugger will be back in Design mode.

##See Also
[Debugging Managed Code][25]

[Debugging Preparation: Visual C++ Project Types][26]

[Debugging Preparation: C#, F#, and Visual Basic Project Types][27]

[Project Settings for a C++ Debug Configuration][28]

[Project Settings for C# Debug Configurations][29]

[Project Settings for a Visual Basic Debug Configuration][30]

[Debugger Security][31]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/ettb6e2a.aspx
[3]: https://msdn.microsoft.com/en-us/library/ms164708.aspx
[4]: https://msdn.microsoft.com/en-us/library/w54zfak1.aspx
[5]: https://msdn.microsoft.com/en-us/library/7sx52ww7.aspx
[6]: https://msdn.microsoft.com/en-us/library/4c8f14c9.aspx
[7]: https://msdn.microsoft.com/en-us/library/cta4x5hc.aspx
[8]: https://msdn.microsoft.com/en-us/library/kbaht4dh.aspx
[9]: https://msdn.microsoft.com/en-us/library/4457htyc.aspx
[10]: https://msdn.microsoft.com/en-us/library/605a12zt.aspx

[11]: https://msdn.microsoft.com/en-us/library/kcw4dzyf.aspx
[12]: https://msdn.microsoft.com/en-us/library/2kf0yb05.aspx
[13]: https://msdn.microsoft.com/en-us/library/2kf0yb05.aspx
[14]: https://msdn.microsoft.com/en-us/library/wx0123s5.aspx
[15]: https://msdn.microsoft.com/en-us/library/605a12zt.aspx
[16]: https://msdn.microsoft.com/en-us/library/kbaht4dh.aspx
[17]: https://msdn.microsoft.com/en-us/library/ms164704.aspx#vxtskdebuggingdllprojectsbuildingadebugversion
[18]: https://msdn.microsoft.com/en-us/library/ms164704.aspx#vxtskdebuggingdllprojectsmixedmodedebugging
[19]: https://msdn.microsoft.com/en-us/library/ms164704.aspx#vxtskdebuggingdllprojectschangingdefaultconfigurations
[20]: https://msdn.microsoft.com/en-us/library/ms164704.aspx#vxtskdebuggingdllprojectschangingdefaultconfigurations
[21]: https://msdn.microsoft.com/en-us/library/ms164704.aspx#vxtskdebuggingdllprojectsthecallingapplication
[22]: https://msdn.microsoft.com/en-us/library/ms164704.aspx#vxtskdebuggingdllprojectscontrolsonawebpage
[23]: https://msdn.microsoft.com/en-us/library/ms164704.aspx#vxtskdebuggingdllprojectstheimmediatewindow
[24]: https://msdn.microsoft.com/en-us/library/ms164704.aspx#NotExistJustToMakeTheAElementVisible

[25]: https://msdn.microsoft.com/en-us/library/awtaffxb.aspx
[26]: https://msdn.microsoft.com/en-us/library/tdb6bs3y.aspx
[27]: https://msdn.microsoft.com/en-us/library/6c38shwk.aspx
[28]: https://msdn.microsoft.com/en-us/library/kcw4dzyf.aspx
[29]: https://msdn.microsoft.com/en-us/library/2kf0yb05.aspx
[30]: https://msdn.microsoft.com/en-us/library/0a10ws2y.aspx
[31]: https://msdn.microsoft.com/en-us/library/ms242231.aspx