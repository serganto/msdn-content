
[Source](https://msdn.microsoft.com/en-us/library/s8y42ktc.aspx "Permalink to Sub or Function not defined (Visual Basic)")

# Sub or Function not defined (Visual Basic) 

A **Sub** or **Function** must be defined in order to be called. Possible causes of this error include:
* Misspelling the procedure name.
* Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.
* Specifying a procedure that is not visible to the calling procedure.
* Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.

## To correct this error

1. Make sure that the procedure name is spelled correctly.

2. Find the name of the project containing the procedure you want to call in the **References** dialog box. If it does not appear, click the **Browse** button to search for it. Select the check box to the left of the project name, and then click **OK**.

3. Check the name of the routine.


##See Also
[Error Types (Visual Basic)][1]

[Managing references in a project][2]

[Sub Statement (Visual Basic)][3] 

[Function Statement (Visual Basic)][4]

[1]: https://msdn.microsoft.com/en-us/library/shz02d41.aspx
[2]: https://msdn.microsoft.com/en-us/library/ez524kew.aspx
[3]: https://msdn.microsoft.com/en-us/library/dz1z94ha.aspx
[4]: https://msdn.microsoft.com/en-us/library/sect4ck6.aspx