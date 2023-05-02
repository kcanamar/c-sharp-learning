# C# Notes

## Creating a Solution
### First, what is a Solution?

A solution is a workspace that combines multiple projects, which are usually related to each other. The construct is very useful in situations when some code needs to be shared among multiple projects.

For example, if you are developing a web site with a separate server-side component, you could segregate it into several related projects:

A project containing common interfaces, producing a DLL
A project containing database definition, producing an RDBMS deployment script
A project containing server-side API implementation, producing an executable
A web site project, producing an IIS deployment script
These four projects are connected to each other. Placing them into a single solution lets you access individual parts, while taking advantage of common indexing that Visual Studio does for you to simplify searches for usage and to help with refactoring.

### How to Create a Solution

**Input**

In a Bash terminal enter the following command. `-n` is the flag for `name`

```bash
dotnet new sln -n "<name of solution>"
```

When you run that command for the first time on your machine you should receive a message similar to the following. 

**Output** 

Welcome to .NET 7.0!
---------------------
SDK Version: 7.0.203

Telemetry
---------
The .NET tools collect usage data in order to help us improve your experience. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry

----------------
Installed an ASP.NET Core HTTPS development certificate.
To trust the certificate run 'dotnet dev-certs https --trust' (Windows and macOS only).
Learn about HTTPS: https://aka.ms/dotnet-https
----------------
Write your first app: https://aka.ms/dotnet-hello-world
Find out what's new: https://aka.ms/dotnet-whats-new
Explore documentation: https://aka.ms/dotnet-docs
Report issues and find source on GitHub: https://github.com/dotnet/core
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli
--------------------------------------------------------------------------------------
The template "Solution File" was created successfully.

## Create a Console Application Project
### What is a Console Application?

An application that takes input and displays output at a command line console with access to three basic data streams: standard input, standard output and standard error.


**Input**

`-n` is the flag for `name`

```bash
dotnet new console -n "<name of project>"
```

**Output**

The template "Console App" was created successfully.

Processing post-creation actions...
Restoring /Users/canamar/dev/development/languages/c#/IntroUI/IntroUI.csproj:
  Determining projects to restore...
  Restored /Users/canamar/dev/development/languages/c#/IntroUI/IntroUI.csproj (in 34 ms).
Restore succeeded.

## Create a class library 
### What is a classlib?

Class libraries are the shared library concept for . NET. 
They enable you to componentize useful functionality into modules that can be used by multiple applications. 
They can also be used as a means of loading functionality that is not needed or not known at application startup.

### How to create a classlib

**Input**

`-n` is the flag for `name`

```bash
dotnet new classlib -n "<library name>"
```

# Connecting Project and Library with Solution 

This uses a glob pattern to add all `.csproj` files to the `.sln` file

**Input**

```bash
dotnet sln VSCodeIntroSln.sln add **/*.csproj   
```

**Output**

Project `IntroLibrary/IntroLibrary.csproj` added to the solution.
Project `IntroUI/IntroUI.csproj` added to the solution.

## Creating a reference to a library from the project directory

**Input**

```bash
dotnet add IntroUI/IntroUI.csproj reference IntroLibrary/IntroLibrary.csproj
```

**Output**

Reference `..\IntroLibrary\IntroLibrary.csproj` added to the project.

## Debugging Settings in VSCode

#### In order to allow access to the terminal to find the .NET SDK
1. Pull down the  Apple menu and choose ‘System Preferences’
2. Go to “Security & Privacy” control panel
3. Select the “Privacy” tab, from the left-side menu select “Full Disk Access”
4. Click the lock icon in the lower left corner and unlock with your auth
5. Click the [+], search for "terminal" and add it. 

Then open the Project directory from the command line with the following code

```bash
code <project directory>
```

This will bring up a prompt in the bottom right hand corner asking 
"Required assets to build and debug are missing from '<Project Directory>'. Add them?"

Select `Yes`, the far right button.

## Note

Repeat this process again in the main directory level with the application/project, library and solution.

**Important** - Be sure to connect the solution to the project and library prior to enabling the vscode debugger/build files to be generated. This will save some headaches later on.

