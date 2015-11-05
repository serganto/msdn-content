
[Source](https://msdn.microsoft.com/en-us/library/vstudio/w67sdsex(v=vs.100).aspx "Permalink to Bind a Windows Forms ComboBox or ListBox Control to Data")

# Bind a Windows Forms ComboBox or ListBox Control to Data


You can bind the [ComboBox][2] and [ListBox][3] to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.

### To bind a ComboBox or ListBox control

1. Set the DataSource property to a data source object. Possible data sources include a [BindingSource][4] bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the [IList][5] interface. For more information, see [Data Sources Supported by Windows Forms][6].

2. If you are binding to a table, set the DisplayMember property to the name of a column in the data source.
\- or -
If you are binding to an [IList][5], set the display member to a public property of the type in the list.
```
	'VB
	Private Sub BindComboBox()
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")
      ComboBox1.DisplayMember = "ProductName"
    End Sub
	
	// C#
    private void BindComboBox()
    {
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];
      comboBox1.DisplayMember = "ProductName";
    }

	// J#
    private void BindComboBox()
    {
       comboBox1.set_DataSource(dataSet1.get_Tables().get_Item(
       "Suppliers"));
       comboBox1.set_DisplayMember("ProductName");
    }
```

>If you are bound to a data source that does not implement the [IBindingList][8] interface, such as an [ArrayList][9], the bound control's data will not be updated when the data source is updated. For example, if you have a combo box bound to an [ArrayList][9] and data is added to the [ArrayList][9], these new items will not appear in the combo box. However, you can force the combo box to be updated by calling the [SuspendBinding][10] and [ResumeBinding][11] methods on the instance of the [BindingContext][12] class to which the control is bound.

##See Also
### Reference
[ComboBox][13]

[ListBox][14]
### Concepts
[Data Binding and Windows Forms][15]
### Other Resources
[Windows Forms Data Binding][16]

[Windows Forms Controls Used to List Options][17]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.combobox(v=vs.100).aspx
[3]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.listbox(v=vs.100).aspx
[4]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingsource(v=vs.100).aspx
[5]: https://msdn.microsoft.com/en-us/library/vstudio/system.collections.ilist(v=vs.100).aspx
[6]: https://msdn.microsoft.com/en-us/library/vstudio/f3y6cb0c(v=vs.100).aspx
[7]: https://i-msdn.sec.s-msft.com/dynimg/IC101471.gif "Note"
[8]: https://msdn.microsoft.com/en-us/library/vstudio/system.componentmodel.ibindinglist(v=vs.100).aspx
[9]: https://msdn.microsoft.com/en-us/library/vstudio/system.collections.arraylist(v=vs.100).aspx
[10]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingmanagerbase.suspendbinding(v=vs.100).aspx
[11]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingmanagerbase.resumebinding(v=vs.100).aspx
[12]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.bindingcontext(v=vs.100).aspx

[13]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.combobox(v=vs.100).aspx
[14]: https://msdn.microsoft.com/en-us/library/vstudio/system.windows.forms.listbox(v=vs.100).aspx
[15]: https://msdn.microsoft.com/en-us/library/vstudio/c8aebh9k(v=vs.100).aspx
[16]: https://msdn.microsoft.com/en-us/library/vstudio/ef2xyb33(v=vs.100).aspx
[17]: https://msdn.microsoft.com/en-us/library/vstudio/zcbed30f(v=vs.100).aspx