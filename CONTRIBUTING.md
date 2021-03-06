# Contributing to the glTF Asset Generator

## Dependencies
1. Install [Visual Studio Code.](https://code.visualstudio.com/Download) (VS Code)
2. Install the VS Code extension [C# for VS Code (powered by OmniSharp)](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
3. Install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2)
4. Install [npm](https://www.npmjs.com/get-npm)

## Set Up
1. Download the repro.
    1. `git clone https://github.com/KhronosGroup/glTF-Asset-Generator.git`
2. Run `npm install` from the [Tools](Tools) folder.
3. Launch VS Code.
    1. Open the local copy of the repro in VS Code.
    2. Select `Explorer` from the sidebar.
    3. Select `Open Folder`.
    4. Select the location of the [glTF-Asset-Generator](https://github.com/KhronosGroup/glTF-Asset-Generator) folder.
5. Press F5 or select `Start Debugging` from the debug menu.

## Best Practices
+ Write readable code.
  + Developers that encounter issues with the models generated by this code will want to look into the code to see how that model is put together.
  + By default, add properties instead of removing properties when creating a model to reduce code complexity.

+ Aim to have fewer than thirteen rows and fewer than seven columns in the model group's readme table (not counting headers).
  + Each model added creates another row. Having too many rows in a table makes it difficult to read due to needing scrolling too much to view the entire model group's readme. Consider splitting the model group into two or more that are closely related.
  + Each property being tested adds another column, and usually adds another model as well. Having too many columns results in results in github's markdown squishing the table to make everything fit.

+ Clearly identify models that are designed to fail to load. (Negative tests)
  + A client that is conformant with the glTF 2.0 spec is expected to successfully render any model created by the glTF Asset Generator, unless explicitly noted otherwise.
  + If a model (or entire group of models) are not expected to load on a conformant client, then the model(s) must be marked as such in the readme.
  + Models that are not valid need the `Valid` bool set to false, even if they are not necessarily expected to fail to load. See "Flag Model as Not Valid" in [Adding Models Advanced](Documents/Adding_Models_Advanced.md).

## Common Errors
+ The error message `Configured debug type 'coreclr'` is encountered when debugging in VS Code
  + This is caused by debugging without [C# for VS Code (powered by OmniSharp)](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) being correctly installed and loaded.
  + Be sure to reload the extension after installing it, or relaunching VS Code.
+ Error message encountered while debugging `Unhandled Exception: System.UnauthorizedAccessException: Access to the path is denied.`
  + A file could not be overwritten.
  + Check that the file isn't open in another program and that it isn't set to readonly.
+ Error message encountered while debugging `An unhandled exception of type 'System.IO.IOException' occurred in System.IO.FileSystem.dll: 'The requested operation cannot be performed on a file with a user-mapped section open'`
    + Encountered when running the debugger again too quickly after having just run it.
    + Wait a few seconds longer between debugging sessions to allow the OS to release its locks on the files.

## Additional Resources
+ [Code Style Guide](Documentation/Code_Style_Guide.md)
+ [Adding Models](Documentation/Adding_Models.md)
+ [Adding Models Advanced](Documentation/Adding_Models_Advanced.md)
+ [Code Flowchart](Source/Resources/Figures/CodeFlowchart.png)
