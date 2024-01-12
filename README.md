# Repo to showcase ASPNET MVC with a failing MVCBuildViews scenario

- intentionally introduced a bad file [BadExcludedView.cshtml](Views/BadExcludedView.cshtml) to the filesystem and excluded from the csproj
- mvc build views still picks it up and fails
```
  MvcBuildViews:
  C:\Windows\Microsoft.NET\Framework\v4.0.30319\aspnet_compiler.exe -v temp -p D:\a\MVCSampleProject\MVCSampleProject 
  C:\Windows\Microsoft.NET\Framework\v4.0.30319\Temporary ASP.NET Files\temp\c635f4d3\27e68a8a\App_Web_stwk4tov.1.cs(31):
  error CS0426: The type name 'DOESNOTEXIST' does not exist in the type 'FilterConfig' [D:\a\MVCSampleProject\MVCSampleProject\MVCSampleProject.csproj]
  Done Building Project "D:\a\MVCSampleProject\MVCSampleProject\MVCSampleProject.csproj" (Rebuild target(s)) -- FAILED.
  Done Building Project "D:\a\MVCSampleProject\MVCSampleProject\MVCSampleProject.sln" (rebuild target(s)) -- FAILED.
  
  Build FAILED.
  ```
