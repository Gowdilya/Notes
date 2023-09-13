Assemblies are the fundamental units of deployment, version control, reuse, activation scoping, and security permissions for .NET-based applications. An assembly is a collection of types and resources that are built to work together and form a logical unit of functionality. Assemblies take the form of executable (_.exe_) or dynamic link library (_.dll_) files, and are the building blocks of .NET applications. They provide the common language runtime with the information it needs to be aware of type implementations.

In .NET and .NET Framework, you can build an assembly from one or more source code files. In .NET Framework, assemblies can contain one or more modules. This way, larger projects can be planned so that several developers can work on separate source code files or modules, which are combined to create a single assembly. For more information about modules, see [How to: Build a multifile assembly](https://learn.microsoft.com/en-us/dotnet/framework/app-domains/build-multifile-assembly).

Assemblies have the following properties:

- Assemblies are implemented as _.exe_ or _.dll_ files.
    
- For libraries that target .NET Framework, you can share assemblies between applications by putting them in the [global assembly cache (GAC)](https://learn.microsoft.com/en-us/dotnet/framework/app-domains/gac). You must strong-name assemblies before you can include them in the GAC. For more information, see [Strong-named assemblies](https://learn.microsoft.com/en-us/dotnet/standard/assembly/strong-named).
    
- Assemblies are only loaded into memory if they're required. If they aren't used, they aren't loaded. Therefore, assemblies can be an efficient way to manage resources in larger projects.
    
- You can programmatically obtain information about an assembly by using reflection. For more information, see [Reflection (C#)](https://learn.microsoft.com/en-us/dotnet/csharp/advanced-topics/reflection-and-attributes/) or [Reflection (Visual Basic)](https://learn.microsoft.com/en-us/dotnet/visual-basic/programming-guide/concepts/reflection).
    
- You can load an assembly just to inspect it by using the [MetadataLoadContext](https://learn.microsoft.com/en-us/dotnet/api/system.reflection.metadataloadcontext) class on .NET and .NET Framework. [MetadataLoadContext](https://learn.microsoft.com/en-us/dotnet/api/system.reflection.metadataloadcontext) replaces the [Assembly.ReflectionOnlyLoad](https://learn.microsoft.com/en-us/dotnet/api/system.reflection.assembly.reflectiononlyload) methods.