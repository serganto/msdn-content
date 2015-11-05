
[Source](https://msdn.microsoft.com/en-us/library/y4x56c0b(v=vs.110).aspx "Permalink to Select an Item in the Windows Forms ListView Control")

# Select an Item in the Windows Forms ListView Control


This example demonstrates how to programmatically select an item in a Windows Forms [ListView][2] control. Selecting an item programmatically does not automatically change the focus to the [ListView][2] control. For this reason, you will typically also want to set the item as focused when selecting an item.

    this.listView1.Items[0].Focused = true;
    this.listView1.Items[0].Selected = true;

##Compiling the Code
This example requires:
* A [ListView][2] control named `listView1` that contains at least one item.
* References to the [System][3] and [System.Windows.Forms][4] namespaces.

##See Also
[ListView][2]

[ListViewItem.Selected][5]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/system.windows.forms.listview(v=vs.110).aspx  
[3]: https://msdn.microsoft.com/en-us/library/system(v=vs.110).aspx
[4]: https://msdn.microsoft.com/en-us/library/system.windows.forms(v=vs.110).aspx
[5]: https://msdn.microsoft.com/en-us/library/system.windows.forms.listviewitem.selected(v=vs.110).aspx