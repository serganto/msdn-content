
[Source](https://msdn.microsoft.com/en-us/library/y0wfd4yz(v=vs.110).aspx "Permalink to Bind Objects to Windows Forms DataGridView Controls")

# Bind Objects to Windows Forms DataGridView Controls


The following code example demonstrates how to bind a collection of objects to a [DataGridView][2] control so that each object displays as a separate row. This example also illustrates how to display a property with an enumeration type in a [DataGridViewComboBoxColumn][3] so that the combo box drop-down list contains the enumeration values.

###CS
    using System;
    using System.Windows.Forms;
    public enum Title
    {
        King,
        Sir
    };
    public class EnumsAndComboBox : Form
    {
        private DataGridView dataGridView1 = new DataGridView();
        private BindingSource bindingSource1 = new BindingSource();

        public EnumsAndComboBox()
        {
            this.Load += new System.EventHandler(EnumsAndComboBox_Load);
        }

        private void EnumsAndComboBox_Load(object sender, System.EventArgs e)
        {
            // Populate the data source.
            bindingSource1.Add(new Knight(Title.King, "Uther", true));
            bindingSource1.Add(new Knight(Title.King, "Arthur", true));
            bindingSource1.Add(new Knight(Title.Sir, "Mordred", false));
            bindingSource1.Add(new Knight(Title.Sir, "Gawain", true));
            bindingSource1.Add(new Knight(Title.Sir, "Galahad", true));

            // Initialize the DataGridView.
            dataGridView1.AutoGenerateColumns = false;
            dataGridView1.AutoSize = true;
            dataGridView1.DataSource = bindingSource1;

            dataGridView1.Columns.Add(CreateComboBoxWithEnums());

            // Initialize and add a text box column.
            DataGridViewColumn column = new DataGridViewTextBoxColumn();
            column.DataPropertyName = "Name";
            column.Name = "Knight";
            dataGridView1.Columns.Add(column);

            // Initialize and add a check box column.
            column = new DataGridViewCheckBoxColumn();
            column.DataPropertyName = "GoodGuy";
            column.Name = "Good";
            dataGridView1.Columns.Add(column);

            // Initialize the form.
            this.Controls.Add(dataGridView1);
            this.AutoSize = true;
            this.Text = "DataGridView object binding demo";
        }

        DataGridViewComboBoxColumn CreateComboBoxWithEnums()
        {
            DataGridViewComboBoxColumn combo = new DataGridViewComboBoxColumn();
            combo.DataSource = Enum.GetValues(typeof(Title));
            combo.DataPropertyName = "Title";
            combo.Name = "Title";
            return combo;
        }
        #region "business object"
        private class Knight
        {
            private string hisName;
            private bool good;
            private Title hisTitle;

            public Knight(Title title, string name, bool good)
            {
                hisTitle = title;
                hisName = name;
                this.good = good;
            }

            public Knight()
            {
                hisTitle = Title.Sir;
                hisName = "<enter name="">";
                good = true;
            }

            public string Name
            {
                get
                {
                    return hisName;
                }

                set
                {
                    hisName = value;
                }
            }

            public bool GoodGuy
            {
                get
                {
                    return good;
                }
                set
                {
                    good = value;
                }
            }

            public Title Title
            {
                get
                {
                    return hisTitle;
                }
                set
                {
                    hisTitle = value;
                }
            }
        }
        #endregion

        [STAThread]
        public static void Main()
        {
            Application.Run(new EnumsAndComboBox());
        }

    }
###VB
```
Imports System.Windows.Forms
Imports System.Collections.Generic
Public Enum Title
    King
    Sir
End Enum
Public Class EnumsAndComboBox
    Inherits Form

    Private flow As New FlowLayoutPanel()
    Private WithEvents checkForChange As Button = New Button()
    Private knights As List(Of Knight)
    Private dataGridView1 As New DataGridView()

    Public Sub New()
        MyBase.New()
        SetupForm()
        SetupGrid()
    End Sub

    Private Sub SetupForm()
        AutoSize = True
    End Sub

    Private Sub SetupGrid()
        knights = New List(Of Knight)
        knights.Add(New Knight(Title.King, "Uther", True))
        knights.Add(New Knight(Title.King, "Arthur", True))
        knights.Add(New Knight(Title.Sir, "Mordred", False))
        knights.Add(New Knight(Title.Sir, "Gawain", True))
        knights.Add(New Knight(Title.Sir, "Galahad", True))

        ' Initialize the DataGridView.
        dataGridView1.AutoGenerateColumns = False
        dataGridView1.AutoSize = True
        dataGridView1.DataSource = knights

        dataGridView1.Columns.Add(CreateComboBoxWithEnums())

        ' Initialize and add a text box column.
        Dim column As DataGridViewColumn = _
            New DataGridViewTextBoxColumn()
        column.DataPropertyName = "Name"
        column.Name = "Knight"
        dataGridView1.Columns.Add(column)

        ' Initialize and add a check box column.
        column = New DataGridViewCheckBoxColumn()
        column.DataPropertyName = "GoodGuy"
        column.Name = "Good"
        dataGridView1.Columns.Add(column)

        ' Initialize the form.
        Controls.Add(dataGridView1)
        Me.AutoSize = True
        Me.Text = "DataGridView object binding demo"
    End Sub

    Private Function CreateComboBoxWithEnums() As DataGridViewComboBoxColumn
        Dim combo As New DataGridViewComboBoxColumn()
        combo.DataSource = [Enum].GetValues(GetType(Title))
        combo.DataPropertyName = "Title"
        combo.Name = "Title"
        Return combo
    End Function

#Region "business object"
    Private Class Knight
        Private hisName As String
        Private good As Boolean
        Private hisTitle As Title

        Public Sub New(ByVal title As Title, ByVal name As String, _
            ByVal good As Boolean)

            hisTitle = title
            hisName = name
            Me.good = good
        End Sub

        Public Property Name() As String
            Get
                Return hisName
            End Get

            Set(ByVal Value As String)
                hisName = Value
            End Set
        End Property

        Public Property GoodGuy() As Boolean
            Get
                Return good
            End Get
            Set(ByVal Value As Boolean)
                good = Value
            End Set
        End Property

        Public Property Title() As Title
            Get
                Return hisTitle
            End Get
            Set(ByVal Value As Title)
                hisTitle = Value
            End Set
        End Property
    End Class
#End Region

    Public Shared Sub Main()
        Application.Run(New EnumsAndComboBox())
    End Sub

End Class
```
##Compiling the Code
This example requires:
* References to the System and System.Windows.Forms assemblies.

For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line (Visual Basic)][4] or [Command-line Building With csc.exe][5]. You can also build this example in Visual Studio by pasting the code into a new project. Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio][6].
##See Also
[DataGridView][2]

[Displaying Data in the Windows Forms DataGridView Control][7]

[How to: Access Objects Bound to Windows Forms DataGridView Rows][8]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/system.windows.forms.datagridview(v=vs.110).aspx
[3]: https://msdn.microsoft.com/en-us/library/system.windows.forms.datagridviewcomboboxcolumn(v=vs.110).aspx
[4]: https://msdn.microsoft.com/en-us/library/25fz1td5(v=vs.110).aspx
[5]: https://msdn.microsoft.com/en-us/library/78f4aasd(v=vs.110).aspx
[6]: https://msdn.microsoft.com/library/Bb129228(v=vs.110)
[7]: https://msdn.microsoft.com/en-us/library/ms171600(v=vs.110).aspx
[8]: https://msdn.microsoft.com/en-us/library/4wszzzc7(v=vs.110).aspx