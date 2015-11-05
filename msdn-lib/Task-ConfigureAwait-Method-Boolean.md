
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

#### SynchronizationContext
Every thread has its own synchronization context. Synchronization context is basically a place or location where code is being executed, however the whole concept is more complicated. Syncronization context is represented by SynchronizationContext class instance which can be obtained for current running thread using SynchronizationContext.Current property. SynchronizationContext can represent not only a thread's context, but also other "places" to execute code, such as certain CPU core. More information about syncronization contexts can be found [here][6].

#### Await default behavior

#### Typical usage
Avoiding GUI applicaitons performance issues
Avoiding deadlock issues

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
