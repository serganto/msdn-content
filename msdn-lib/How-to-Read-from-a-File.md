
[Source](https://msdn.microsoft.com/en-us/library/db5x7c0d(v=vs.110).aspx)

# Read Text from a File

The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps. In both examples, when you create the instance of the [StreamReader][2] class, you provide the relative or absolute path to the file. The following examples assume that the file named TestFile.txt is in the same folder as the application.

These code examples do not apply developing for Windows Store Apps because the Windows Runtime provides different streams types reading and writing to files. For an example that shows how to read text from a file within the context of a Windows Store app, see [Quickstart: Reading and writing files][3]. For examples that show how to convert between .NET Framework streams and Windows runtime streams see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams][4].

The first example shows a synchronous read operation within a console application. In this example, the text file is opened using a stream reader, the contents are copied to a string and string is output to the console.

    using System;
    using System.IO;

    class Test
    {
        public static void Main()
        {
            try
            {   // Open the text file using a stream reader.
                using (StreamReader sr = new StreamReader("TestFile.txt"))
                {
    	        // Read the stream to a string, and write the string to the console.
                    String line = sr.ReadToEnd();
                    Console.WriteLine(line);
                }
            }
            catch (Exception e)
            {
                Console.WriteLine("The file could not be read:");
                Console.WriteLine(e.Message);
            }
        }
    }

The second example shows an asynchronous read operation within a Windows Presentation Foundation (WPF) application.

    using System;
    using System.Windows;
    using System.IO;

    namespace WpfApplication
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void ReadFileButton_Click(object sender, RoutedEventArgs e)
            {
                try
                {
                    using (StreamReader sr = new StreamReader("TestFile.txt"))
                    {
                        String line = await sr.ReadToEndAsync();
                        ResultBlock.Text = line;
                    }
                }
                catch (Exception ex)
                {
                    ResultBlock.Text = "Could not read the file";
                }
            }
        }
    }

## See Also
<p><a href="https://msdn.microsoft.com/en-us/library/system.io.streamreader(v=vs.110).aspx">StreamReader</a><br><a href="https://msdn.microsoft.com/en-us/library/system.io.file.opentext(v=vs.110).aspx">File<span xmlns="">.</span>OpenText</a><br><a href="https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline(v=vs.110).aspx">StreamReader<span xmlns="">.</span>ReadLine</a><br><a href="https://msdn.microsoft.com/en-us/library/kztecsys(v=vs.110).aspx">Asynchronous File I/O</a><br><a href="https://msdn.microsoft.com/en-us/library/5cf8zcfh(v=vs.110).aspx">NIB: How to: Create a Directory Listing</a><br><a href="https://msdn.microsoft.com/library/windows/apps/hh758325.aspx">Quickstart: Reading and writing files</a><br><a href="https://msdn.microsoft.com/en-us/library/dn531021(v=vs.110).aspx">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</a><br><a href="https://msdn.microsoft.com/en-us/library/36b93480(v=vs.110).aspx">How to: Read and Write to a Newly Created Data File</a><br><a href="https://msdn.microsoft.com/en-us/library/3zc0w663(v=vs.110).aspx">How to: Open and Append to a Log File</a><br><a href="https://msdn.microsoft.com/en-us/library/6ka1wd3w(v=vs.110).aspx">How to: Write Text to a File</a><br><a href="https://msdn.microsoft.com/en-us/library/9yyz8a6c(v=vs.110).aspx">How to: Read Characters from a String</a><br><a href="https://msdn.microsoft.com/en-us/library/z4kzt0dd(v=vs.110).aspx">How to: Write Characters to a String</a><br><a href="https://msdn.microsoft.com/en-us/library/k3352a4t(v=vs.110).aspx">File and Stream I/O</a><br></p>

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/system.io.streamreader(v=vs.110).aspx
[3]: https://msdn.microsoft.com/library/windows/apps/hh758325.aspx
[4]: https://msdn.microsoft.com/en-us/library/dn531021(v=vs.110).aspx
  