Alternative/Shared Static File Path in ASP.Net
=======================================
In Startup.cs:

```c#
//using for our custom static path.
using Microsoft.AspNet.StaticFiles;
using Microsoft.AspNet.FileProviders;
using System.IO;

...

string altStatic = "/path/to/your/static/files";
if(Directory.Exists(altStatic)){              
  app.UseStaticFiles(new StaticFileOptions() { FileProvider = new PhysicalFileProvider(altStatic) } );
}
app.UseStaticFiles(); //Also check the wwwroot directory after our shared directory.
```

And in the dependencies of the project.json (valid on May 2, 2016):
```
"Microsoft.AspNet.FileProviders.Abstractions": "1.0.0-rc1-final"
```

This is useful for when you have e.g. an existing apache httpd server running and want to share static
files. Obviously of little use for containers.

