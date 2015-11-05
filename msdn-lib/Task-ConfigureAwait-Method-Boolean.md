
[Source](https://msdn.microsoft.com/en-us/library/hh195037(l=en-us,v=VS.110).aspx)

# Task.ConfigureAwait Method (Boolean) (System.Threading.Tasks)

Configures an awaiter used to await this [Task][1].

**Namespace:**
[System.Threading.Tasks][2]  
**Assembly:**
mscorlib (in mscorlib.dll)

##Syntax
    public ConfiguredTaskAwaitable ConfigureAwait(
    	bool continueOnCapturedContext
    )

#### Parameters

*continueOnCapturedContext*

Type: [System.Boolean][3]

**true** to attempt to marshal the continuation back to the original context captured; otherwise, **false**.

#### Return Value
Type: [System.Runtime.CompilerServices.ConfiguredTaskAwaitable][5]

An object used to await this task.

## Remarks

#### Synchronization context

Every thread has its own synchronization context. Synchronization context is basically a place or location where code is being executed, however the whole concept is more complicated. Syncronization context is represented by **SynchronizationContext** class instance which can be obtained for current running thread with the **SynchronizationContext.Current** property. **SynchronizationContext** class can represent not only a thread's context, but also other "places" to execute code, such as certain CPU core. **SynchronizationContext** can be used to pass code to execute from one thread to another one as well.

More information about synchronization contexts can be found [here][6]. A good explanation is also in [MSDN Magazine][7].

#### **await** default behavior in terms of synchronization context

**await** significantly simplifies asynchronous programming, but it is important to understand its behavior in terms of synchronization context, because improper use can lead to unpredictable code behavior, such as weird unhandled exceptions, especially in multi-threaded GUI applications.

A good explanation of async programming can be found [in this article][8].

By default, if we use **await** when running a [Task][9] instance, it first captures a current thread's synchronization context, then blocks the current thread and runs the task, so the calling thread is being awaited until execution finishes. After that the rest part of the caller method is invoked with the **same synchronization context captured before**, i.e. exactly in that thread which initiated async method call. Running the rest part of calling method in the same synchronization context by default is important part of await behavior.

#### Executing in the same context can be undesirable

In some cases the same context execution can be undesirable because it can produce deadlocks situations. Consider the following C# code example which shows what happens if you block synchronous code on task execution:

```
public static class Example
{
	static async Task DelayTask()
	{
		await Task.Delay(1000);
	}
	public static async void ThisCallForcesDeadlock()
	{
		DelayTask().Wait();
		MessageBox.Show("Task completed");
	}
}
```

The demo is for Windows Forms application, but it will show the problem in any UI application such as ASP.NET and so on. If you call the **ThisCallForcesDeadlock()** method you will never see a message box.

The problem is an UI application has default synchronization context which allows to execute only one piece of code simultaneously. So what happens in the example is that **Task.Delay()** is executed and it is waiting for UI synchronization context to be free to continue execution in the context. But simultaneously **DelayTask.Wait()** blocks the same context waiting for **Task.Delay()** to be finished. So we have a deadlock situation here.

You can follow [here][10] for a real-world sample and even more detailed explanation.

Notice: the code won't produce any issues in a console application because of different context management. Console applications have synchronization context which allows to run multiple code units at one time.

There are two ways to fix the problem. We either use await everywhere in the code instead of synchronous blocks or use **ConfigureAwait(false)** to avoid executing the continuation in the same context.

So both code samples below will solve the issue.

```
public static class Example
{
	static async Task DelayTask()
	{
		await Task.Delay(1000).ConfigureAwait(false);
	}
	public static async void ThisCallForcesDeadlock()
	{
		DelayTask().Wait();
		MessageBox.Show("Task completed");
	}
}
```

```
public static class Example
{
	static async Task DelayTask()
	{
		await Task.Delay(1000);
	}
	public static async void ThisCallForcesDeadlock()
	{
		await DelayTask();
		MessageBox.Show("Task completed");
	}
}
```

When we use **ConfigureAwait(false)** we explicitly say not to continue the execution for **Task.Delay()** call in the same context.

#### Typical usage

1. As mentioned before, the main use case is to avoid any deadlocks.
2. Executing continuation in the same context in GUI apps can produce performance issues in case of intensive use of asynchronous calls because all continuations will be forwarded to single UI thread. **ConfigureAwait(false)** can solve the problem as well.

#### Use cases

The Azure Machine Learning request/response web service example contains the following code to avoid a deadlock:

```
// WARNING: The 'await' statement below can result in a deadlock if you are calling this code from the UI thread of an ASP.Net application.
// One way to address this would be to call ConfigureAwait(false) so that the execution does not attempt to resume on the original context.
// For instance, replace code such as:
//      result = await DoSomeTask()
// with the following:
//      result = await DoSomeTask().ConfigureAwait(false)
```

##Version Information
**Universal Windows Platform**

Available since 4.5

  
**.NET Framework**

Available since 4.5

  
**Portable Class Library**

Supported in:

[portable .NET platforms][4]  
**Windows Phone Silverlight**

Available since 8.0

  
**Windows Phone**

Available since 8.1
##See Also
<p><a href="https://msdn.microsoft.com/en-us/library/system.threading.tasks.task(v=vs.110).aspx">Task Class</a><br><a href="https://msdn.microsoft.com/en-us/library/system.threading.tasks(v=vs.110).aspx">System.Threading.Tasks Namespace</a><br></p>

[1]: https://msdn.microsoft.com/en-us/library/system.threading.tasks.task(v=vs.110).aspx
[2]: https://msdn.microsoft.com/en-us/library/system.threading.tasks(v=vs.110).aspx
[3]: https://msdn.microsoft.com/en-us/library/system.boolean(v=vs.110).aspx
[4]: https://msdn.microsoft.com/en-us/library/gg597391.aspx
[5]: https://msdn.microsoft.com/en-us/library/system.runtime.compilerservices.configuredtaskawaitable(v=vs.110).aspx
[6]: https://msdn.microsoft.com/en-us/library/system.threading.synchronizationcontext(v=vs.110).aspx
[7]: https://msdn.microsoft.com/magazine/gg598924.aspx
[8]: https://msdn.microsoft.com/en-us/library/vstudio/hh191443(v=vs.110).aspx
[9]: https://msdn.microsoft.com/en-us/library/system.threading.tasks.task(v=vs.110).aspx
[10]: http://blog.stephencleary.com/2012/07/dont-block-on-async-code.html
