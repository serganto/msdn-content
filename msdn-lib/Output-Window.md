[Source](https://msdn.microsoft.com/en-us/library/3hk6fby3.aspx "Permalink to Output Window")

# Output Window
 

The **Output** window can display status messages for various features in the integrated development environment (IDE). To open the **Output** window, on the menu bar, choose **View/Output** (or click CTRL + ALT + O).

>The Output window does not appear on the View menu in Visual Studio Express editions. To bring it up, use the hotkey CTRL + ALT + O.


**Show output from**
:

Displays one or more output panes to view. Several panes of information might be available, depending on which tools in the IDE have used the **Output** window to deliver messages to the user.

**Find Message in Code** 
:

Moves the insertion point in the code editor to the line that contains the selected build error.

**Go to Previous Message** 
:

Changes the focus in the **Output** window to the previous build error and moves the insertion point in the code editor to the line that contains that build error.

**Go to Next Message** 
:

Changes the focus in the **Output** window to the next build error and moves the insertion point in the code editor to the line that contains that build error.

**Clear all** 
:

Clears all text from the **Output** pane.

**Toggle Word Wrap** 
:

Turns the Word Wrap feature on and off in the **Output** pane. When Word Wrap is on, text in longer entries that extends beyond the viewing area is displayed on the following line.
##Output Pane
The **Output** pane selected in the **Show output from** list displays output from the source indicated.
##Routing Messages to the Output Window
To display the **Output** window whenever you build a project, in the **General, Projects and Solutions, Options** dialog box, select **Show Output window when build starts**. Then, with a code file open for editing, choose the **Go to Next Message** and **Go To Previous Message** buttons on the **Output** window toolbar to select entries in the **Output** pane. As you do this, the insertion point in the code editor jumps to the line of code where the selected problem occurs.

Certain IDE features and commands invoked in the [Command Window][3] deliver their output to the **Output** window. Output from external tools such as .bat and .com files, which is typically displayed in the Command Prompt window, is routed to an **Output** pane when you select the **Use Output Window** option in the [Managing External Tools][4]. Many other kinds of messages can be displayed in **Output** panes as well. For example, when Transact-SQL syntax in a stored procedure is checked against a target database, the results are displayed in the **Output** window.

You can also program your own applications to write diagnostic messages at run time to an **Output** pane. To do this, use members of the [Debug][5] class or [Trace][6] class in the [System.Diagnostics][7] namespace of the .NET Framework Class Library. Members of the [Debug][5] class display output when you build Debug configurations of your solution or project; members of the [Trace][6] class display output when you build either Debug or Release configurations. For more information, see [Diagnostic Messages in the Output Window][8].

In Visual C++, you can create custom build steps and build events whose warnings and errors are displayed and counted in the **Output** pane. By pressing F1 on a line of output, you can display an appropriate help topic. For more information, see [Formatting the Output of a Custom Build Step or Build Event][9].

##Scrolling Behavior
If you use autoscrolling in the Output window and then navigate by using the mouse or arrow keys, autoscrolling stops. To resume autoscrolling, press CTRL+END.

##See Also
[Diagnostic Messages in the Output Window][10]

[How to: Control the Output Window][11]

[Compiling and Building in Visual Studio][12]

[Understanding Build Configurations][13]

[.NET Framework Class Library Overview][14]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://i-msdn.sec.s-msft.com/dynimg/IC174466.jpeg "System_CAPS_warning"
[3]: https://msdn.microsoft.com/en-us/library/c785s0kz.aspx
[4]: https://msdn.microsoft.com/en-us/library/76712d27.aspx
[5]: https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx
[6]: https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx
[7]: https://msdn.microsoft.com/en-us/library/system.diagnostics.aspx
[8]: https://msdn.microsoft.com/en-us/library/bs4c1wda.aspx
[9]: https://msdn.microsoft.com/en-us/library/yxkt8b26.aspx

[10]: https://msdn.microsoft.com/en-us/library/bs4c1wda.aspx
[11]: https://msdn.microsoft.com/en-us/library/ht6z4e28.aspx
[12]: https://msdn.microsoft.com/en-us/library/cyz1h6zd.aspx
[13]: https://msdn.microsoft.com/en-us/library/kkz9kefa.aspx
[14]: https://msdn.microsoft.com/en-us/library/kkz9kefa.aspx