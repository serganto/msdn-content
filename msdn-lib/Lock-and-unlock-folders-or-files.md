[Source](https://msdn.microsoft.com/en-us/library/ms181420.aspx "Permalink to Lock and unlock folders or files")

# Lock and unlock folders or files


A folder or file can be locked or unlocked to deny or restore the user's privileges. Privileges include checking out an item for edit into a different workspace or checking in Pending Changes to an item from a different workspace. For more information, see [Create and work with workspaces][2].

You can use a lock to temporarily freeze the server version of an item so that you can check in a [pending change][3] without having to resolve any merge conflicts. If you want to permanently prevent access to an item on the server, you should use the [Permission Command][4] instead.

>You can use the [Lock command][6] to remove another user's lock if you have sufficient permissions.


**Requirements**

See [Pernission reference for Team Foundation Server][7].

### To lock a folder or file from Source Control Explorer

1. On the View menu, choose Other Windows,and then choose Source Control Explorer.

You can also double-click Source Control in Team Explorer.

2. In Source Control Explorer, in a workspace, open the shortcut menu for the folder or file to which you want to apply a lock, and then choose Lock.

3. In the Lock dialog box select the file or folder you want.

4. Choose either the Check Out lock or the Check In lock type, and then choose Lock.

For more information, see [Understand lock types][8].

Under Pending Changes, Source Control Explorer displays the status: lock. The next time pending changes are checked in, the lock will take affect. For more information, see [Check in your work to the team's codebase][9].

>You can also lock folders and files from the command line. For more information, see [Lock Command][6].

### To unlock a folder or file from Source Control Explorer

1. On the View menu, choose Other Windows,and then choose Source Control Explorer.

2. In Source Control Explorer, open the shortcut menu for the folder or file from which you want to remove a lock, and then choose Unlock.

##See Also
Other Resources

[Understand lock types][11]

[Lock Command][12]

[Use Source Control Explorer to manage files under version control][13]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/ms181383.aspx
[3]: https://msdn.microsoft.com/en-us/library/ms245462.aspx
[4]: https://msdn.microsoft.com/en-us/library/0dsd05ft.aspx
[5]: https://i-msdn.sec.s-msft.com/areas/global/content/clear.gif "Tip"
[6]: https://msdn.microsoft.com/en-us/library/47b0c7w9.aspx
[7]: https://msdn.microsoft.com/en-us/library/ms252587.aspx
[8]: https://msdn.microsoft.com/en-us/library/ms181419.aspx
[9]: https://msdn.microsoft.com/en-us/library/ms181407.aspx
[10]: https://i-msdn.sec.s-msft.com/areas/global/content/clear.gif "Note"

[11]: https://msdn.microsoft.com/en-us/library/ms181419.aspx
[12]: https://msdn.microsoft.com/en-us/library/47b0c7w9.aspx
[13]: https://msdn.microsoft.com/en-us/library/ms181370.aspx