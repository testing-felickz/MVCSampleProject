# Repo to showcase ASPNET MVC with a failing MVCBuildViews scenario

- intentionally introduced a bad file [BadExcludedView.cshtml](Views/BadExcludedView.cshtml) to the filesystem and excluded from the csproj
- mvc build views is [set to false](https://github.com/testing-felickz/MVCSampleProject/blob/bea1153cfba3a6248f9a401b4eebc1980ac385bb/MVCSampleProject.csproj#L18C3-L18C41) still picks it up and fails when executing [build target](https://github.com/testing-felickz/MVCSampleProject/blob/bea1153cfba3a6248f9a401b4eebc1980ac385bb/MVCSampleProject.csproj#L219C1-L221C12) via (`/p:MvcBuildViews=true`)
```
  MvcBuildViews:
  C:\Windows\Microsoft.NET\Framework\v4.0.30319\aspnet_compiler.exe -v temp -p D:\a\MVCSampleProject\MVCSampleProject 
  C:\Windows\Microsoft.NET\Framework\v4.0.30319\Temporary ASP.NET Files\temp\c635f4d3\27e68a8a\App_Web_stwk4tov.1.cs(31):
  error CS0426: The type name 'DOESNOTEXIST' does not exist in the type 'FilterConfig' [D:\a\MVCSampleProject\MVCSampleProject\MVCSampleProject.csproj]
  Done Building Project "D:\a\MVCSampleProject\MVCSampleProject\MVCSampleProject.csproj" (Rebuild target(s)) -- FAILED.
  Done Building Project "D:\a\MVCSampleProject\MVCSampleProject\MVCSampleProject.sln" (rebuild target(s)) -- FAILED.
  
  Build FAILED.
  ```

# Fixes
- Various techniques as specified in [Codeql-Troubleshooting](https://github.com/advanced-security/advanced-security-material/blob/main/troubleshooting/codeql-builds/compiled-languages-csharp.md#mvcbuildviews-target-failures) are shown in different PRs: https://github.com/testing-felickz/MVCSampleProject/pulls
