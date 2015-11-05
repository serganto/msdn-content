
[Source](https://msdn.microsoft.com/en-us/library/yc4fsbf5(v=vs.110).aspx)

# Get and Set the Current Cell in the Windows Forms DataGridView Control

Interaction with the [DataGridView][2] often requires that you programmatically discover which cell is currently active. You may also need to change the current cell. You can perform these tasks with the [CurrentCell][3] property.

>You cannot set the current cell in a row or column that has its [Visible][5] property set to **false**.


Depending on the [DataGridView][2] control's selection mode, changing the current cell can change the selection. For more information, see [Selection Modes in the Windows Forms DataGridView Control][6].

## To get the current cell programmatically

* Use the [DataGridView][2] control's [CurrentCell][3] property.
```
    private void getCurrentCellButton_Click(object sender, System.EventArgs e)
    {
        string msg = String.Format("Row: {0}, Column: {1}",
            dataGridView1.CurrentCell.RowIndex,
            dataGridView1.CurrentCell.ColumnIndex);
        MessageBox.Show(msg, "Current Cell");
    }
```

## To set the current cell programmatically

* Set the [CurrentCell][3] property of the [DataGridView][2] control. In the following code example, the current cell is set to row 0, column 1.
```
    private void setCurrentCellButton_Click(object sender, System.EventArgs e)
    {
        // Set the current cell to the cell in column 1, Row 0.
        this.dataGridView1.CurrentCell = this.dataGridView1[1,0];
    }
```

## Compiling the Code

This example requires:

* [Button][7] controls named getCurrentCellButton and setCurrentCellButton. In Visual C#, you must attach the [Click][8] events for each button to the associated event handler in the example code.
* A [DataGridView][2] control named dataGridView1.
* References to the [System][9] and [System.Windows.Forms][10] assemblies.

##See Also
[DataGridView][11]

[DataGridView.CurrentCell][12]

[Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control][13]

[Selection Modes in the Windows Forms DataGridView Control][14]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/system.windows.forms.datagridview(v=vs.110).aspx
[3]: https://msdn.microsoft.com/en-us/library/system.windows.forms.datagridview.currentcell(v=vs.110).aspx
[4]: https://i-msdn.sec.s-msft.com/dynimg/IC101471.jpeg "System_CAPS_note"
[5]: https://msdn.microsoft.com/en-us/library/system.windows.forms.datagridviewband.visible(v=vs.110).aspx
[6]: https://msdn.microsoft.com/en-us/library/8x6w9028(v=vs.110).aspx
[7]: https://msdn.microsoft.com/en-us/library/system.windows.forms.button(v=vs.110).aspx
[8]: https://msdn.microsoft.com/en-us/library/system.windows.forms.control.click(v=vs.110).aspx
[9]: https://msdn.microsoft.com/en-us/library/system(v=vs.110).aspx
[10]: https://msdn.microsoft.com/en-us/library/system.windows.forms(v=vs.110).aspx

[11]: https://msdn.microsoft.com/en-us/library/system.windows.forms.datagridview(v=vs.110).aspx
[12]: https://msdn.microsoft.com/en-us/library/system.windows.forms.datagridview.currentcell(v=vs.110).aspx
[13]: https://msdn.microsoft.com/en-us/library/ms171596(v=vs.110).aspx
[14]: https://msdn.microsoft.com/en-us/library/8x6w9028(v=vs.110).aspx
