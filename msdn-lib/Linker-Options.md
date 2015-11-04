[Source](https://msdn.microsoft.com/en-us/library/y0zzbyt4.aspx "Permalink to Linker Options")

# Linker Options

LINK.exe links Common Object File Format (COFF) object files and libraries to create an executable (.exe) file or a dynamic-link library (DLL).

The following table lists options for LINK.exe. For more information about LINK, see:

* [Compiler-Controlled LINK Options][90]
* [LINK Input Files][91]
* [LINK Output][92]
* [Reserved Words][93]

On the command line, linker options are not case-sensitive—for example, /base and /BASE mean the same thing. For details on how to specify each option on the command line or in Visual Studio, see the documentation for that option.

| Option | Purpose |
| :------------- |:-------------|
|[@][1]| Specifies a response file.
|[/ALIGN][2] |Specifies the alignment of each section. |
|[/ALLOWBIND][3] |Specifies that a DLL cannot be bound. |
|[/ALLOWISOLATION][4] |Specifies behavior for manifest lookup. |
|[/APPCONTAINER][5] |Specifies whether the app must run within an appcontainer process environment. |
|[/ASSEMBLYDEBUG][6] |Adds the [DebuggableAttribute][7] to a managed image. |
|[/ASSEMBLYLINKRESOURCE][8] |Creates a link to a managed resource. |
|[/ASSEMBLYMODULE][9] |Specifies that a Microsoft intermediate language (MSIL) module should be imported into the assembly. |
|[/ASSEMBLYRESOURCE][10] |Embeds a managed resource file in an assembly. |
|[/BASE][11] |Sets a base address for the program. |
|[/CGTHREADS][12] |Sets number of cl.exe threads to use for optimization and code generation when link-time code generation is specified. |
|[/CLRIMAGETYPE][13] |Sets the type (IJW, pure, or safe) of a CLR image. |
|[/CLRSUPPORTLASTERROR][14] |Preserves the last error code of functions that are called through the P/Invoke mechanism. |
|[/CLRTHREADATTRIBUTE][15]  |Specifies the threading attribute to apply to the entry point of your CLR program. |
|[/CLRUNMANAGEDCODECHECK][16] |Specifies whether the linker will apply the SuppressUnmanagedCodeSecurity attribute to linker-generated PInvoke stubs that call from managed code into native DLLs. |
|[/DEBUG][17] |Creates debugging information. |
|[/DEBUGTYPE][18] |Specifies which data to include in debugging information. |
|[/DEF][19] |Passes a module-definition (.def) file to the linker. |
|[/DEFAULTLIB][20] |Searches the specified library when external references are resolved. |
|[/DELAY][21] |Controls the delayed loading of DLLs. |
|[/DELAYLOAD][22] |Causes the delayed loading of the specified DLL. |
|[/DELAYSIGN][23] |Partially signs an assembly. |
|[/DLL][24] |Builds a DLL. |
|[/DRIVER][25] |Creates a kernel mode driver. |
|[/DYNAMICBASE][26] |Specifies whether to generate an executable image that can be randomly rebased at load time by using the address space layout randomization (ASLR) feature. |
|[/ENTRY][27] |Sets the starting address. |
|[/errorReport][28] |Reports internal linker errors to Microsoft. |
|[/EXPORT][29] |Exports a function. |
|[/FIXED][30] |Creates a program that can be loaded only at its preferred base address. |
|[/FORCE][31] |Forces a link to complete even with unresolved symbols or symbols defined more than once. |
|[/FUNCTIONPADMIN][32] |Creates an image that can be hot patched. |
|[/GENPROFILE, /FASTGENPROFILE][33] |Both of these options specify generation of a .pgd file by the linker to support profile-guided optimization (PGO). /GENPROFILE and /FASTGENPROFILE use different default parameters. |
|[/GUARD][34] |Enables Control Flow Guard protection. |
|[/HEAP][35] |Sets the size of the heap, in bytes. |
|[/HIGHENTROPYVA][36] |Specifies support for high-entropy 64-bit address space layout randomization (ASLR). |
|[/IDLOUT][37] |Specifies the name of the .idl file and other MIDL output files. |
|[/IGNORE][38] |Suppresses output of specified linker warnings. |
|[/IGNOREIDL][39] |Prevents the processing of attribute information into an .idl file. |
|[/IMPLIB][40] |Overrides the default import library name. |
|[/INCLUDE][41] |Forces symbol references. |
|[/INCREMENTAL][42] |Controls incremental linking. |
|[/INTEGRITYCHECK][43] |Specifies that the module requires a signature check at load time. |
|[/KEYCONTAINER][44] |Specifies a key container to sign an assembly. |
|[/KEYFILE][45] |Specifies a key or key pair to sign an assembly. |
|[/LARGEADDRESSAWARE][46] |Tells the compiler that the application supports addresses larger than two gigabytes |
|[/LIBPATH][47] |Specifies a path to search before the environmental library path. |
|[/LTCG][48] |Specifies link-time code generation. |
|[/MACHINE][49] |Specifies the target platform. |
|[/MANIFEST][50] |Creates a side-by-side manifest file and optionally embeds it in the binary. |
|[/MANIFESTDEPENDENCY][51] |Specifies a  section in the manifest file. |
|[/MANIFESTFILE][52] |Changes the default name of the manifest file. |
|[/MANIFESTINPUT][53] |Specifies a manifest input file for the linker to process and embed in the binary. You can use this option multiple times to specify more than one manifest input file. |
|[/MANIFESTUAC][54] |Specifies whether User Account Control (UAC) information is embedded in the program manifest. |
|[/MAP][55] |Creates a mapfile. |
|[/MAPINFO][56] |Includes the specified information in the mapfile. |
|[/MERGE][57] |Combines sections. |
|[/MIDL][58] |Specifies MIDL command-line options. |
|[/NOASSEMBLY][59] |Suppresses the creation of a .NET Framework assembly. |
|[/NODEFAULTLIB][60] |Ignores all (or the specified) default libraries when external references are resolved. |
|[/NOENTRY][61] |Creates a resource-only DLL. |
|[/NOLOGO][62] |Suppresses the startup banner. |
|[/NXCOMPAT][63] |Marks an executable as verified to be compatible with the Windows Data Execution Prevention feature. |
|[/OPT][64] |Controls LINK optimizations. |
|[/ORDER][65] |Places COMDATs into the image in a predetermined order. |
|[/OUT][66] |Specifies the output file name. |
|[/PDB][67] |Creates a program database (PDB) file. |
|[/PDBALTPATH][68] |Uses an alternate location to save a PDB file. |
|[/PDBSTRIPPED][69] |Creates a program database (PDB) file that has no private symbols. |
|[/PGD][70] |Specifies a .pgd file for profile-guided optimizations. |
|[/PROFILE][71]  |Produces an output file that can be used with the Performance Tools profiler. |
|[/RELEASE][72] |Sets the Checksum in the .exe header. |
|[/SAFESEH][73] |Specifies that the image will contain a table of safe exception handlers. |
|[/SECTION][74] |Overrides the attributes of a section. |
|[/STACK][75] |Sets the size of the stack in bytes. |
|[/STUB][76] |Attaches an MS-DOS stub program to a Win32 program. |
|[/SUBSYSTEM][77] |Tells the operating system how to run the .exe file. |
|[/SWAPRUN][78] |Tells the operating system to copy the linker output to a swap file before it is run. |
|[/TLBID][79] |Specifies the resource ID of the linker-generated type library. |
|[/TLBOUT][80] |Specifies the name of the .tlb file and other MIDL output files. |
|[/TSAWARE][81] |Creates an application that is designed specifically to run under Terminal Server. |
|[/VERBOSE][82] |Prints linker progress messages. |
|[/VERSION][83] |Assigns a version number. |
|[/WINMD][84] |Enables generation of a Windows Runtime Metadata file. |
|[/WINMDFILE][85] |Specifies the file name for the Windows Runtime Metadata (winmd) output file that's generated by the [/WINMD][84] linker option. |
|[/WINMDKEYFILE][86] |Specifies a key or key pair to sign a Windows Runtime Metadata file. |
|[/WINMDKEYCONTAINER][87] |Specifies a key container to sign a Windows Metadata file. |
|[/WINMDDELAYSIGN][88] |Partially signs a Windows Runtime Metadata (.winmd) file by placing the public key in the winmd file. |
|[/WX][89] |Treats linker warnings as errors. |

For more information, see [Compiler-Controlled LINK Options][90].

##See Also
[C/C++ Building Reference][94]

[Setting Linker Options][95]

[Frequently Asked Questions on Building][96]

[1]: https://msdn.microsoft.com/en-us/library/4xdcbak7.aspx
[2]: https://msdn.microsoft.com/en-us/library/8xx65e1y.aspx
[3]: https://msdn.microsoft.com/en-us/library/hsa130k8.aspx
[4]: https://msdn.microsoft.com/en-us/library/daa1w5yk.aspx
[5]: https://msdn.microsoft.com/en-us/library/dn195768.aspx
[6]: https://msdn.microsoft.com/en-us/library/cta4x5hc.aspx
[7]: https://msdn.microsoft.com/en-us/library/system.diagnostics.debuggableattribute.aspx
[8]: https://msdn.microsoft.com/en-us/library/ztd4k98t.aspx
[9]: https://msdn.microsoft.com/en-us/library/6de7xtwd.aspx
[10]: https://msdn.microsoft.com/en-us/library/yzdy7b10.aspx
[11]: https://msdn.microsoft.com/en-us/library/f7f5138s.aspx
[12]: https://msdn.microsoft.com/en-us/library/dn655038.aspx
[13]: https://msdn.microsoft.com/en-us/library/31zwwc39.aspx
[14]: https://msdn.microsoft.com/en-us/library/yy0hww86.aspx
[15]: https://msdn.microsoft.com/en-us/library/s6bz81ya.aspx
[16]: https://msdn.microsoft.com/en-us/library/ms173523.aspx
[17]: https://msdn.microsoft.com/en-us/library/xe4t6fc1.aspx
[18]: https://msdn.microsoft.com/en-us/library/dn823750.aspx
[19]: https://msdn.microsoft.com/en-us/library/34c30xs1.aspx
[20]: https://msdn.microsoft.com/en-us/library/229a6ysd.aspx
[21]: https://msdn.microsoft.com/en-us/library/hdx9xk46.aspx
[22]: https://msdn.microsoft.com/en-us/library/yx9zd12s.aspx
[23]: https://msdn.microsoft.com/en-us/library/bk4wd6yz.aspx
[24]: https://msdn.microsoft.com/en-us/library/527z7zfs.aspx
[25]: https://msdn.microsoft.com/en-us/library/43a6z8s4.aspx
[26]: https://msdn.microsoft.com/en-us/library/bb384887.aspx
[27]: https://msdn.microsoft.com/en-us/library/f9t8842e.aspx
[28]: https://msdn.microsoft.com/en-us/library/ms235602.aspx
[29]: https://msdn.microsoft.com/en-us/library/7k30y2k5.aspx
[30]: https://msdn.microsoft.com/en-us/library/w368ysh2.aspx
[31]: https://msdn.microsoft.com/en-us/library/70abkas3.aspx
[32]: https://msdn.microsoft.com/en-us/library/ms173524.aspx
[33]: https://msdn.microsoft.com/en-us/library/mt574047.aspx
[34]: https://msdn.microsoft.com/en-us/library/dn919634.aspx
[35]: https://msdn.microsoft.com/en-us/library/f90ybzkh.aspx
[36]: https://msdn.microsoft.com/en-us/library/dn195771.aspx
[37]: https://msdn.microsoft.com/en-us/library/cf540x82.aspx
[38]: https://msdn.microsoft.com/en-us/library/dn782850.aspx
[39]: https://msdn.microsoft.com/en-us/library/f2bt983c.aspx
[40]: https://msdn.microsoft.com/en-us/library/67wc07b9.aspx
[41]: https://msdn.microsoft.com/en-us/library/2s3hwbhs.aspx
[42]: https://msdn.microsoft.com/en-us/library/4khtbfyf.aspx
[43]: https://msdn.microsoft.com/en-us/library/dn195769.aspx
[44]: https://msdn.microsoft.com/en-us/library/5k6bd8t1.aspx
[45]: https://msdn.microsoft.com/en-us/library/x730hw3t.aspx
[46]: https://msdn.microsoft.com/en-us/library/wz223b1z.aspx
[47]: https://msdn.microsoft.com/en-us/library/1xhzskbe.aspx
[48]: https://msdn.microsoft.com/en-us/library/xbf3tbeh.aspx
[49]: https://msdn.microsoft.com/en-us/library/5wy54dk2.aspx
[50]: https://msdn.microsoft.com/en-us/library/f2c0w594.aspx
[51]: https://msdn.microsoft.com/en-us/library/ew0y5khy.aspx
[52]: https://msdn.microsoft.com/en-us/library/fft52235.aspx
[53]: https://msdn.microsoft.com/en-us/library/dn195770.aspx
[54]: https://msdn.microsoft.com/en-us/library/bb384691.aspx
[55]: https://msdn.microsoft.com/en-us/library/k7xkk3e2.aspx
[56]: https://msdn.microsoft.com/en-us/library/bha0yc3d.aspx
[57]: https://msdn.microsoft.com/en-us/library/wxz26dz2.aspx
[58]: https://msdn.microsoft.com/en-us/library/9kae41s3.aspx
[59]: https://msdn.microsoft.com/en-us/library/df0y9bww.aspx
[60]: https://msdn.microsoft.com/en-us/library/3tz4da4a.aspx
[61]: https://msdn.microsoft.com/en-us/library/8ys34d7t.aspx
[62]: https://msdn.microsoft.com/en-us/library/ef4d60dk.aspx
[63]: https://msdn.microsoft.com/en-us/library/ms235442.aspx
[64]: https://msdn.microsoft.com/en-us/library/bxwfs976.aspx
[65]: https://msdn.microsoft.com/en-us/library/00kh39zz.aspx
[66]: https://msdn.microsoft.com/en-us/library/8htcy933.aspx
[67]: https://msdn.microsoft.com/en-us/library/kwx19e36.aspx
[68]: https://msdn.microsoft.com/en-us/library/dd998269.aspx
[69]: https://msdn.microsoft.com/en-us/library/y87kw2fd.aspx
[70]: https://msdn.microsoft.com/en-us/library/438sd1tf.aspx
[71]: https://msdn.microsoft.com/en-us/library/ays5x7b0.aspx
[72]: https://msdn.microsoft.com/en-us/library/h8ksa72a.aspx
[73]: https://msdn.microsoft.com/en-us/library/9a89h429.aspx
[74]: https://msdn.microsoft.com/en-us/library/sf9b18xk.aspx
[75]: https://msdn.microsoft.com/en-us/library/8cxs58a6.aspx
[76]: https://msdn.microsoft.com/en-us/library/7z0585h5.aspx
[77]: https://msdn.microsoft.com/en-us/library/fcc1zstk.aspx
[78]: https://msdn.microsoft.com/en-us/library/chzz5ts6.aspx
[79]: https://msdn.microsoft.com/en-us/library/b1kw34cb.aspx
[80]: https://msdn.microsoft.com/en-us/library/439ahd3s.aspx
[81]: https://msdn.microsoft.com/en-us/library/01cfys9z.aspx
[82]: https://msdn.microsoft.com/en-us/library/wdsk6as6.aspx
[83]: https://msdn.microsoft.com/en-us/library/h88b7dc8.aspx
[84]: https://msdn.microsoft.com/en-us/library/jj157268.aspx
[85]: https://msdn.microsoft.com/en-us/library/jj157265.aspx
[86]: https://msdn.microsoft.com/en-us/library/jj157267.aspx
[87]: https://msdn.microsoft.com/en-us/library/jj157269.aspx
[88]: https://msdn.microsoft.com/en-us/library/jj157266.aspx
[89]: https://msdn.microsoft.com/en-us/library/ms235592.aspx

[90]: https://msdn.microsoft.com/en-us/library/92b5ab4h.aspx
[91]: https://msdn.microsoft.com/en-us/library/hcce369f.aspx
[92]: https://msdn.microsoft.com/en-us/library/37b80k4a.aspx
[93]: https://msdn.microsoft.com/en-us/library/163abkbh.aspx 

[94]: https://msdn.microsoft.com/en-us/library/91621w01.aspx
[95]: https://msdn.microsoft.com/en-us/library/wk97ab1b.aspx
[96]: https://msdn.microsoft.com/en-us/library/t2ys1khs.aspx