
[Source](https://msdn.microsoft.com/en-us/library/bb397755(v=vs.110).aspx)

# Write User Settings at Run Time with C#


Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions. Settings that are user-scoped, however, can be written at run time just as you would change any property value. The new value persists for the duration of the application session. You can persist the changes to the settings between application sessions by calling the Save method.

## How To: Write and Persist User Settings at Run Time with C#

1. Access the setting and assign it a new value as shown in this example:
```
    // C#
    Properties.Settings.Default.myColor = Color.AliceBlue;
```
2. If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:
```
    // C#
    Properties.Settings.Default.Save();
```
User settings are saved in a file within a subfolder of the user's local hidden application data folder.

##See Also
<p><a href="https://msdn.microsoft.com/en-us/library/bb397750(v=vs.110).aspx">Using Application Settings and User Settings</a><br><a href="https://msdn.microsoft.com/en-us/library/bb397759(v=vs.110).aspx">How To: Read Settings at Run Time With C#</a><br><a href="https://msdn.microsoft.com/en-us/library/k4s6c3a0(v=vs.110).aspx">Application Settings Overview</a><br></p>
[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
  