---
title: project.json reference
description: project.json reference
keywords: .NET, .NET Core, project.json
author: aL3891
manager: wpickett
ms.date: 07/06/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3aef32bd-ee2a-4e24-80f8-a2b615e0336d
---

# project.json reference

> [!NOTE]
> This topic is preliminary and subject to change in the next release. You can track the status of this issue through our public GitHub issue tracker.

## Overview

    {
        "[name](#name)": String,
        "[version](#version)": String,
        "[description](#description)": String,
        "[copyright](#copyright)": String,
        "[title](#title)": String,
        "[entryPoint](#entryPoint)": String,
        "[testRunner](#testRunner)": String,
        "[authors](#authors)": String[],
        "[language](#language)": String,
        "[embedInteropTypes](#embedInteropTypes)": Boolean,
        "[preprocess](#preprocess)": String or String[],
        "[shared](#shared)": String or String[],
        "[dependencies](#dependencies)": Object,
        "[tools](#tools)": Object,
        "[scripts](#scripts)": Object,
        "[buildOptions](#buildOptions)": Object {
            "[define](#buildOptions.define)": String[],
            "[nowarn](#buildOptions.nowarn)": String[],
            "[additionalArguments](#buildOptions.additionalArguments)": String[],
            "[warningsAsErrors](#buildOptions.warningsAsErrors)": Boolean,
            "[allowUnsafe](#buildOptions.allowUnsafe)": Boolean,
            "[emitEntryPoint](#buildOptions.emitEntryPoint)": Boolean,
            "[optimize](#buildOptions.optimize)": Boolean,
            "[platform](#buildOptions.platform)": String,
            "[languageVersion](#buildOptions.languageVersion)": String,
            "[keyFile](#buildOptions.keyFile)": String,
            "[delaySign](#buildOptions.delaySign)": Boolean,
            "[publicSign](#buildOptions.publicSign)": Boolean,
            "[debugType](#buildOptions.debugType)": String,
            "[xmlDoc](#buildOptions.xmlDoc)": Boolean,
            "[preserveCompilationContext](#buildOptions.preserveCompilationContext)": Boolean,
            "[outputName](#buildOptions.outputName)": String,
            "[compilerName](#buildOptions.compilerName)": String,
            "[compile](#buildOptions.compile)": Object {
                "[include](#buildOptions.compile.include)": String or String[],
                "[exclude](#buildOptions.compile.exclude)": String or String[],
                "[includeFiles](#buildOptions.compile.includeFiles)": String or String[],
                "[excludeFiles](#buildOptions.compile.excludeFiles)": String or String[],
                "[builtIns](#buildOptions.compile.builtIns)": Object,
                "[mappings](#buildOptions.compile.mappings)": Object
            },
            "[embed](#buildOptions.embed)": Object {
                "[include](#buildOptions.embed.include)": String or String[],
                "[exclude](#buildOptions.embed.exclude)": String or String[],
                "[includeFiles](#buildOptions.embed.includeFiles)": String or String[],
                "[excludeFiles](#buildOptions.embed.excludeFiles)": String or String[],
                "[builtIns](#buildOptions.embed.builtIns)": Object,
                "[mappings](#buildOptions.embed.mappings)": Object
            },
            "[copyToOutput](#buildOptions.copyToOutput)": Object {
                "[include](#buildOptions.copyToOutput.include)": String or String[],
                "[exclude](#buildOptions.copyToOutput.exclude)": String or String[],
                "[includeFiles](#buildOptions.copyToOutput.includeFiles)": String or String[],
                "[excludeFiles](#buildOptions.copyToOutput.excludeFiles)": String or String[],
                "[builtIns](#buildOptions.copyToOutput.builtIns)": Object,
                "[mappings](#buildOptions.copyToOutput.mappings)": Object
            }
        },
        "[publishOptions](#publishOptions)": Object {
            "[include](#publishOptions.include)": String or String[],
            "[exclude](#publishOptions.exclude)": String or String[],
            "[includeFiles](#publishOptions.includeFiles)": String or String[],
            "[excludeFiles](#publishOptions.excludeFiles)": String or String[],
            "[builtIns](#publishOptions.builtIns)": Object,
            "[mappings](#publishOptions.mappings)": Object
        },
        "[runtimeOptions](#runtimeOptions)": Object {
            "[configProperties](#runtimeOptions.configProperties)": Object {
                "[System.GC.Server](#runtimeOptions.configProperties.System.GC.Server)": Boolean,
                "[System.GC.Concurrent](#runtimeOptions.configProperties.System.GC.Concurrent)": Boolean,
                "[System.GC.RetainVM](#runtimeOptions.configProperties.System.GC.RetainVM)": Boolean,
                "[System.Threading.ThreadPool.MinThreads](#runtimeOptions.configProperties.System.Threading.ThreadPool.MinThreads)": Integer,
                "[System.Threading.ThreadPool.MaxThreads](#runtimeOptions.configProperties.System.Threading.ThreadPool.MaxThreads)": Integer
            },
            "[framework](#runtimeOptions.framework)": Object {
                "[name](#runtimeOptions.framework.name)": String,
                "[version](#runtimeOptions.framework.version)": String,
            },
            "[applyPatches](#runtimeOptions.applyPatches)": Boolean
        },
        "[packOptions](#packOptions)": Object {
            "[summary](#packOptions.summary)": String,
            "[tags](#packOptions.tags)": String[],
            "[owners](#packOptions.owners)": String[],
            "[releaseNotes](#packOptions.releaseNotes)": String,
            "[iconUrl](#packOptions.iconUrl)": String,
            "[projectUrl](#packOptions.projectUrl)": String,
            "[licenseUrl](#packOptions.licenseUrl)": String,
            "[requireLicenseAcceptance](#packOptions.requireLicenseAcceptance)": Boolean,
            "[repository](#packOptions.repository)": Object {
                "[type](#packOptions.repository.type)": String,
                "[url](#packOptions.repository.url)": String
            },
            "[files](#packOptions.files)": Object {
                "[include](#packOptions.files.include)": String or String[],
                "[exclude](#packOptions.files.exclude)": String or String[],
                "[includeFiles](#packOptions.files.includeFiles)": String or String[],
                "[excludeFiles](#packOptions.files.excludeFiles)": String or String[],
                "[builtIns](#packOptions.files.builtIns)": Object,
                "[mappings](#packOptions.files.mappings)": Object
            }
        },
        "[analyzerOptions](#analyzerOptions)": Object {
            "[languageId](#analyzerOptions.languageId)": String
        },
        "[configurations](#configurations)": Object,
        "[frameworks](#frameworks)": Object {
            "[dependencies](#frameworks.dependencies)": Object,
            "[frameworkAssemblies](#frameworks.frameworkAssemblies)": Object,
            "[wrappedProject](#frameworks.wrappedProject)": String,
            "[bin](#frameworks.bin)": Object,
            "[imports](#frameworks.imports)": String
        }
    }

<a name="name"></a>
## name
Type: String

The name of the project, used for the assembly name as well as the name of the package. The top level folder name is used if this property is not specified.

For example:

```json
{
    "name": "MyLibrary"
}
```

<a name="version"></a>
## version
Type: String

The [Semver](http://semver.org/spec/v1.0.0.html) version of the project, also used for the NuGet package.

For example:

```json
{
    "version": "1.0.0-*"
}
```

<a name="description"></a>
## description
Type: String

A longer description of the project. Used in the assembly properties.

For example:

```json
{
    "description": "This is my library and it's really great!"
}
```

<a name="copyright"></a>
## copyright
Type: String

The copyright information for the project. Used in the assembly properties.

For example:

```json
{
    "copyright": "Fabrikam 2016"
}
```

<a name="title"></a>
## title
Type: String

The friendly name of the project, can contain spaces and special characters not allowed when using the `name` property. Used in the assembly properties.

For example:

```json
{
    "title": "My Library"
}
```

<a name="entryPoint"></a>
## entryPoint
Type: String

The entrypoint method for the project. `Main` by default.

For example:

```json
{
    "entryPoint": "ADifferentMethod"
}
```
    
<a name="testRunner"></a>
## testRunner
Type: String

The name of the test runner, such as [NUnit](http://nunit.org/) or [xUnit](http://xunit.github.io/), to use with this project. Setting this also marks the project as a test project.

For example:

```json
{
    "testRunner": "NUnit"
}
```

<a name="authors"></a>
## authors
Type: String[]

An array of strings with the names of the authors of the project.

For example:

```json
{
    "authors": ["Anne", "Bob"]
}
```

<a name="language"></a>
## language
Type: String

The (human) language of the project. Corresponds to the "neutral-language" compiler argument.

For example:

```json
{
    "language": "en-US"
}
```

<a name="embedInteropTypes"></a>
## embedInteropTypes
Type: Boolean

`true` to embed COM interop types in the assembly; otherwise, `false`. 

For example:

```json
{
    "embedInteropTypes": true
}
```

<a name="preprocess"></a>
## preprocess
Type: String or String[] with a globbing pattern

Specifies which files are included in preprocessing.

For example:

```json
{
    "preprocess": "compiler/preprocess/**/*.cs"
}
```

<a name="shared"></a>
## shared
Type: String or String[] with a globbing pattern

Specifies which files are shared, this is used for library export.

For example:

```json
{
    "shared": "shared/**/*.cs"
}
```

<a name="dependencies"></a>
## dependencies
Type: Object

An object that defines the package dependencies of the project, each key of this object is the name of a package and each value contains versioning information.

For example:

```json
    "dependencies": {
        "System.Reflection.Metadata": "1.3.0",
        "Microsoft.Extensions.JsonParser.Sources": {
          "type": "build",
          "version": "1.0.0-rc2-20221"
        },
        "Microsoft.Extensions.HashCodeCombiner.Sources": {
          "type": "build",
          "version": "1.1.0-alpha1-21456"
        },
        "Microsoft.Extensions.DependencyModel": "1.0.0-*"
    }
```

<a name="tools"></a>
## tools
Type: Object

An object that defines package dependencies that are used as tools for the current project, not as references. Packages defined here are available in scripts that run during the build process, but they are not accessible to the code in the project itself. Tools can for example include code generators or post-build tools that perform tasks related to packing.

For example:

```json
{
    "tools": {
    "MyObfuscator": "1.2.4"
    }
}
```

<a name="scripts"></a>
## scripts
Type: Object

An object that defines scripts run during the build process. Each key in this object identifies where in the build the script is run. Each value is either a string with the script to run or an array of strings containing scripts that will run in order.
The supported events are:
* precompile
* postcompile
* prepublish
* postpublish

For example:

```json
{
    "scripts": {
        "precompile": "generateCode.cmd",
        "postcompile": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
    }
}
```

<a name="buildOptions"></a>
## buildOptions
Type: Object

An object whose properties control various aspects of compilation. The valid properties are listed below. Can also be specified per target framework as described in the [frameworks section](#frameworks).

For example:

```json
    "buildOptions": {
      "allowUnsafe": true,
      "emitEntryPoint": true
    }
```

<a name="buildOptions.define"></a>
### define
Type: String[]

A list of defines such as "DEBUG" or "TRACE" that can be used in conditional compilation in the code.

For example:

```json
{
    "buildOptions": {
        "define": ["TEST", "OTHERCONDITION"]
    }
}
```

<a name="buildOptions.nowarn"></a>
### nowarn
Type: String[]

A list of warnings to ignore.

For example:

```json
{
    "buildOptions": {
        "nowarn": ["CS0168", "CS0219"]
    }
}
```

This ignores the warnings `The variable 'var' is assigned but its value is never used` and `The variable 'var' is assigned but its value is never used`

<a name="buildOptions.additionalArguments"></a>
### additionalArguments
Type: String[]

A list of extra arguments that will be passed to the compiler.

For example:

```json
{
    "buildOptions": {
        "additionalArguments": ["/parallel", "/nostdlib"]
    }
}
```

<a name="buildOptions.warningsAsErrors"></a>
### warningsAsErrors
Type: Boolean

`true` to treat warnings as errors; otherwise, `false`. The default is `false`.

For example:

```json
{
    "buildOptions": {
        "warningsAsErrors": true
    }
}
```

<a name="buildOptions.allowUnsafe"></a>
### allowUnsafe
Type: Boolean

`true` to allow unsafe code in this project; otherwise, `false`. The default is `false`.

For example:

```json
{
    "buildOptions": {
        "allowUnsafe": true
    }
}
```

<a name="buildOptions.emitEntryPoint"></a>
### emitEntryPoint
Type: Boolean

`true` to create an executable; `false` to produce a `.dll` file. The default is `false`.

For example:

```json
{
    "buildOptions": {
        "emitEntryPoint": true
    }
}
```

<a name="buildOptions.optimize"></a>
### optimize
Type: Boolean

`true` to enable the compiler to optimize the code in this project; otherwise, `false`. The default is `false`.

For example:

```json
{
    "buildOptions": {
        "optimize": true
    }
}
```

<a name="buildOptions.platform"></a>
### platform
Type: String

The name of the target platform, such as AnyCpu, x86 or x64.

For example:

```json
{
    "buildOptions": {
        "platform": "x64"
    }
}
```

<a name="buildOptions.languageVersion"></a>
### languageVersion
Type: String

The version of the language used by the compiler: ISO-1, ISO-2, 3, 4, 5, 6, or Default

For example:

```json
{
    "buildOptions": {
        "languageVersion": "5"
    }
}
```

<a name="buildOptions.keyFile"></a>
### keyFile
Type: String

The path for the key file used for signing this assembly.

For example:

```json
{
    "buildOptions": {
        "keyFile": "../keyfile.snk"
    }
}
```

<a name="buildOptions.delaySign"></a>
### delaySign
Type: Boolean

`true` to delay signing; otherwise, `false`. The default is `false`.

For example:

```json
{
    "buildOptions": {
        "delaySign": true
    }
}
```

<a name="buildOptions.publicSign"></a>
### publicSign
Type: Boolean

`true` to enable signing of the resulting assembly; otherwise, `false`. The default is `false`.

For example:

```json
{
    "buildOptions": {
        "publicSign": true
    }
}
```

<a name="buildOptions.debugType"></a>
### debugType
Type: String

Indicates the type of symbol file (PDB file) to generate. The options are "portable" (for .NET Core projects) or "full" (the traditional Windows-only PDB files).

For example:

```json
{
    "buildOptions": {
        "debugType": "portable"
    }
}
```

<a name="buildOptions.xmlDoc"></a>
### xmlDoc
Type: Boolean

`true` to generate XML documentation from triple-slash comments in the source code; otherwise, `false`. The default is `false`.

For example:

```json
{
    "buildOptions": {
        "xmlDoc": true
    }
}
```

<a name="buildOptions.preserveCompilationContext"></a>
### preserveCompilationContext
Type: Boolean

`true` to preserve reference assemblies and other context data to allow for runtime compilation; otherwise, `false`. The default is `false`.

For example:

```json
{
    "buildOptions": {
        "preserveCompilationContext": true
    }
}
```

<a name="buildOptions.outputName"></a>
### outputName
Type: String

Change the name of the output file. 

For example:

```json
{
    "buildOptions": {
        "outputName": "MyApp"
    }
}
```

<a name="buildOptions.compilerName"></a>
### compilerName
Type: String

The name of the compiler used for this project. `csc` by default. Currently, `csc` (the C# compiler) or `fsc` (the F# compiler) are supported.
 
For example:

```json
{
    "compilerName": "fsc"
}
```
    
<a name="buildOptions.compile"></a>
### compile
Type: Object

An object containing properties for compilation configuration.

<a name="buildOptions.compile.include"></a>
#### include
Type: String or String[] with a globbing pattern.

Specifies which files to include in the build. The patterns are rooted at the project folder. Defaults to none.

For example:

```json
{
    "include":["wwwroot", "Views"]
}
```

<a name="buildOptions.compile.exclude"></a>
#### exclude
Type: String or String[] with a globbing pattern.

Specifies which files to exclude from the build. The exclude patterns have higher priority than the include patterns, so a file found in both will be excluded. The patterns are rooted at the project folder. Defaults to none.

For example:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

<a name="buildOptions.compile.includeFiles"></a>
#### includeFiles

Type: String or String[] with a globbing pattern.

A list of file paths to include. The paths are rooted at the project folder. This list has a higher priority than the include and exclude globbing patterns, hence a file listed here and in the exclude globbing pattern will still be included. Defaults to none.

For example:

```json
{
    "includeFiles": []
}
```

<a name="buildOptions.compile.excludeFiles"></a>
#### excludeFiles

Type: String or String[] with a globbing pattern.

A list of file paths to exclude. The paths are rooted at the project folder. This list has a higher priority than globbing patterns and the include paths, hence a file found in all will be excluded. Defaults to none.

For example:

```json
{
    "excludeFiles":[],
}
```

<a name="buildOptions.compile.builtIns"></a>
#### builtIns

Type: Object

The defaults provided by the system. It can have `include` and `exclude` globbing patterns which are merged with the corresponding values of the `include` and `exclude` properties.

For example:

```json
{
    "builtIns":{}
}
```

<a name="buildOptions.compile.mappings"></a>
#### mappings
Type: Object

Keys to the object represent destination paths in the output layout.

Values are either a string or an object representing the source path of files to include.  The object represtation can have its own `include`, `exclude`, `includeFiles` and `excludeFiles` sections.

String example:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Object example:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

<a name="buildOptions.embed"></a>
### embed
Type: Object

An object containing properties for compilation configuration.

<a name="buildOptions.embed.include"></a>
#### include
Type: String or String[] with a globbing pattern.

```json
{
    "include":["wwwroot", "Views"]
}
```

<a name="buildOptions.embed.exclude"></a>
#### exclude
Type: String or String[] with a globbing pattern.

Specifies which files to exclude from the build.

For example:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

<a name="buildOptions.embed.includeFiles"></a>
#### includeFiles

Type: String or String[] with a globbing pattern.

```json
{
    "includeFiles":[],
}
```

<a name="buildOptions.embed.excludeFiles"></a>
#### excludeFiles

Type: String or String[] with a globbing pattern.

```json
{
    "excludeFiles":[],
}
```

<a name="buildOptions.embed.builtIns"></a>
#### builtIns
Type: Object

```json
{
    "builtIns":{}
}
```

<a name="buildOptions.embed.mappings"></a>
#### mappings
Type: Object

Keys to the object represent destination paths in the output layout.

Values are either a string or an object representing the source path of files to include.  The object represtation can have its own `include`, `exclude`, `includeFiles` and `excludeFiles` sections.

String example:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Object example:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

<a name="buildOptions.copyToOutput"></a>
### copyToOutput
Type: Object

An object containing properties for compilation configuration.

<a name="buildOptions.copyToOutput.include"></a>
#### include
Type: String or String[] with a globbing pattern.

```json
{
    "include":["wwwroot", "Views"]
}
```

<a name="buildOptions.copyToOutput.exclude"></a>
#### exclude
Type: String or String[] with a globbing pattern.

Specifies which files to exclude from the build.

For example:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

<a name="buildOptions.copyToOutput.includeFiles"></a>
#### includeFiles

Type: String or String[] with a globbing pattern.

```json
{
    "includeFiles":[],
}
```

<a name="buildOptions.copyToOutput.excludeFiles"></a>
#### excludeFiles

Type: String or String[] with a globbing pattern.

```json
{
    "excludeFiles":[],
}
```

<a name="buildOptions.copyToOutput.builtIns"></a>
#### builtIns
Type: Object

```json
{
    "builtIns":{}
}
```

<a name="buildOptions.copyToOutput.mappings"></a>
#### mappings
Type: Object

Keys to the object represent destination paths in the output layout.

Values are either a string or an object representing the source path of files to include.  The object represtation can have its own `include`, `exclude`, `includeFiles` and `excludeFiles` sections.

String example:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Object example:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

<a name="publishOptions"></a>
## publishOptions
Type: Object

An object containing properties for compilation configuration.

<a name="publishOptions.include"></a>
### include
Type: String or String[] with a globbing pattern.

```json
{
    "include":["wwwroot", "Views"]
}
```

<a name="publishOptions.exclude"></a>
### exclude
Type: String or String[] with a globbing pattern.

Specifies which files to exclude from the build.

For example:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

<a name="publishOptions.includeFiles"></a>
### includeFiles

Type: String or String[] with a globbing pattern.

```json
{
    "includeFiles":[],
}
```

<a name="publishOptions.excludeFiles"></a>
### excludeFiles

Type: String or String[] with a globbing pattern.

```json
{
    "excludeFiles":[],
}
```

<a name="publishOptions.builtIns"></a>
### builtIns
Type: Object

```json
{
    "builtIns":{}
}
```

<a name="publishOptions.mappings"></a>
### mappings
Type: Object

Keys to the object represent destination paths in the output layout.

Values are either a string or an object representing the source path of files to include.  The object represtation can have its own `include`, `exclude`, `includeFiles` and `excludeFiles` sections.

String example:

```json
{
    "mappings": {
        "dest/file": "./src/file",
        "dest/folder/": "./src/folder/**/*"
    }
}
```

Object example:

```json
{
    "mappings": {
        "dest/file":{
            "include":"./src/file"
        },
        "dest/folder/":{
            "include":"./src/folder/**/*"
        }
    }
}
```

<a name="runtimeOptions"></a>
## runtimeOptions
Type: Object

Specifies parameters to be provided to the runtime during initialization.

<a name="runtimeOptions.configProperties"></a>
### configProperties
Type: Object

Contains configuration properties to configure the runtime and the framework.

<a name="runtimeOptions.configProperties.System.GC.Server"></a>
#### System.GC.Server
Type: Boolean

`true` to enable server garbage collection; otherwise, `false`. The default is `false`.

For example:

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Server": true
        }
    }
}
```

<a name="runtimeOptions.configProperties.System.GC.Concurrent"></a>
#### System.GC.Concurrent
Type: Boolean

`true` to enable concurrent garbage collection; otherwise, `false`. The default is `false`.

For example:

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Concurrent": true
        }
    }
}
```

<a name="runtimeOptions.configProperties.System.GC.RetainVM"></a>
#### System.GC.RetainVM
Type: Boolean

`true` to put segments that should be deleted on a standby list for future use instead of releasing them back to the operating system (OS); otherwise, `false`.

For example:

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.RetainVM": true
        }
    }
}
```

<a name="runtimeOptions.configProperties.System.Threading.ThreadPool.MinThreads"></a>
#### System.Threading.ThreadPool.MinThreads
Type: Integer

Overrides the number of minimum threads for the ThreadPool worker pool.

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MinThreads": 4
        }
    }
}
```

<a name="runtimeOptions.configProperties.System.Threading.ThreadPool.MaxThreads"></a>
#### System.Threading.ThreadPool.MaxThreads
Type: Integer

Overrides the number of maximum threads for the ThreadPool worker pool.

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MaxThreads": 25
        }
    }
}
```

<a name="runtimeOptions.framework"></a>
### framework
Type: Object

Contains shared framework properties to use when activating the application. The presence of this section indicates that the application is a portable app designed to use a shared redistributable framework.

<a name="runtimeOptions.framework.name"></a>
#### name
Type: String

Name of the shared framework.

```json
{
    "runtimeOptions": {
        "framework": {
            "name": "Microsoft.DotNetCore"
        }
    }
}
```

<a name="runtimeOptions.framework.version"></a>
#### version
Type: String

Version of the shared framework.

```json
{
    "runtimeOptions": {
        "framework": {
            "version": "1.0.1"
        }
    }
}
```

<a name="runtimeOptions.applyPatches"></a>
### applyPatches
Type: Boolean

`true` to use the framework from either the same or a higher version that differs only in the `SemVer` patch field. `false` for the host to use only the exact framework version. The default is `true`.

```json
{
    "runtimeOptions": {
        "applyPatches": false
    }
}
```

<a name="packOptions"></a>
## packOptions
Type: Object

Defines options pertaining to the packaging of the project output into a NuGet package.

<a name="packOptions.summary"></a>
### summary
Type: String

A short description of the project.

For example:

```json
{
    "packOptions": {
        "summary": "This is my library."
    }
}
```

<a name="packOptions.tags"></a>
### tags
Type: String[]

An array of strings with tags for the project, used for searching in NuGet.

For example:

```json
{
    "packOptions": {
        "tags": ["hyperscale", "cats"]
    }
}
```

<a name="packOptions.owners"></a>
### owners
Type: String[]

An array of strings with the names of the owners of the project.

For example:

```json
{
    "packOptions": {
        "owners": ["Fabrikam", "Microsoft"]
    }
}
```

<a name="packOptions.releaseNotes"></a>
### releaseNotes
Type: String

Release notes for the project.

For example:

```json
{
    "packOptions": {
        "releaseNotes": "Initial version, implemented flimflams."
    }
}
```

<a name="packOptions.iconUrl"></a>
### iconUrl
Type: String

The URL for an icon that will be used in various places such as the package explorer.

For example:

```json
{
    "packOptions": {
        "iconUrl": "http://www.mylibrary.gov/favicon.ico"
    }
}
```

<a name="packOptions.projectUrl"></a>
### projectUrl
Type: String

The URL for the homepage of the project.

For example:

```json
{
    "packOptions": {
        "projectUrl": "http://www.mylibrary.gov"
    }
}
```

<a name="packOptions.licenseUrl"></a>
### licenseUrl
Type: String

The URL for the license the project uses.

For example:

```json
{
    "packOptions": {
        "licenseUrl": "http://www.mylibrary.gov/licence"
    }
}
```

<a name="packOptions.requireLicenseAcceptance"></a>
### requireLicenseAcceptance
Type: Boolean

`true` to cause a prompt to accept the package license when installing the package to be shown; otherwise, `false`. Only used for NuGet packages, ignored in other uses. The default is `false`.

For example:

```json
{
    "packOptions": {
        "requireLicenseAcceptance": true
    }
}
```
   
<a name="packOptions.repository"></a>
### repository
Type: Object

Contains information about the repository where the project is stored.

<a name="packOptions.repository.type"></a>
#### type
Type: String

Type of the repository. The default value is "git".

For example:

```json
{
    "packOptions": {
        "repository": {
            "type": "git"
        }
    }
}
```

<a name="packOptions.repository.url"></a>
#### url
Type: String

URL of the repository where the project is stored.

For example:

```json
{
    "packOptions": {
        "repository": {
            "url": "http://github.com/dotnet/corefx"
        }
    }
}
```

<a name="packOptions.files"></a>
### files
Type: Object

<a name="packOptions.files.include"></a>
#### include
Type: String or String[] with a globbing pattern.

```json
{
    "include":["wwwroot", "Views"]
}
```

<a name="packOptions.files.exclude"></a>
#### exclude
Type: String or String[] with a globbing pattern.

Specifies which files to exclude from the build.

For example:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

<a name="packOptions.files.includeFiles"></a>
#### includeFiles

Type: String or String[] with a globbing pattern.

```json
{
    "includeFiles":[]
}
```

<a name="packOptions.files.excludeFiles"></a>
#### excludeFiles

Type: String or String[] with a globbing pattern.

```json
{
    "excludeFiles":[]
}
```

<a name="packOptions.files.builtIns"></a>
#### builtIns
Type: Object

```json
{
    "builtIns":{}
}
```

<a name="packOptions.files.mappings"></a>
#### mappings
Type: Object

Keys to the object represent destination paths in the output layout.

Values are either a string or an object representing the source path of files to include.  The object representation can have its own `include`, `exclude`, `includeFiles` and `excludeFiles` sections. 

String example:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Object example:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

<a name="analyzerOptions"></a>
## analyzerOptions
Type: Object

An object with properties used by code analysers.

For example:

```json
{
    "analyzerOptions": { }
}
```

<a name="analyzerOptions.languageId"></a>
### languageId
Type: String

The id of the language to analyze. "cs" represents C#, "vb" represents Visual Basic and "fs" represents F#.

For example:

```json
"analyzerOptions": {
    "languageId": "vb"
}
```

<a name="configurations"></a>
## configurations
Type: Object

An object whose properties define different configurations for this project, such as Debug and Release. Each value is an object that can contain a `buildOptions` object with options specific for this configuration.

For example:

```json
"configurations": {
    "Release": {
        "buildOptions": {
            "allowUnsafe": false
        }
    }
}
```

<a name="frameworks"></a>
## frameworks
Type: Object

Specifies which frameworks this project supports, such as the .NET Framework or Universal Windows Platform (UWP). Must be a valid Target Framework Moniker (TFM). Each value is an object that can contain information specific to this framework such as `buildOptions`, `analyzerOptions`, `dependencies` as well as the properties in the following sections.

For example:

```json
"frameworks": {
    "netcoreapp1.0": {
        "buildOptions": {
            "define": ["FOO", "BIZ"]
        }
    }
}
```

<a name="frameworks.dependencies"></a>
### dependencies
Type: Object

Dependencies that are specific for this framework. This is useful in scenarios where you cannot simply specify a package-level dependency across all targets. Reasons for this can include one target lacking built-in support that other targets have, or requiring a different version of a dependency than other targets.

For example:

```json
    "frameworks": {
        "netstandard1.5": {
        "dependencies": {
            "Microsoft.Extensions.JsonParser.Sources": "1.0.0-rc2-20221"
        }
    }
}
```

<a name="frameworks.frameworkAssemblies"></a>
### frameworkAssemblies
Type: Object

Similar to dependencies but contains reference to assemblies in the GAC that are not NuGet packages. Can also specify the version to use as well as the dependency type. This is used when targeting .NET Framework and Portable Class Library (PCL) targets. You can only build a project with this specified on Windows.

For example:

```json
"frameworks": {
    "net451": {
        "frameworkAssemblies": {
            "System.Runtime": {
                "type": "build",
                "version": "4.0.0"
            }
        }
    }
}
```

<a name="frameworks.wrappedProject"></a>
### wrappedProject
Type: String

Specifies the location of the dependency project. 

For example:

```json
"frameworks": {
    "net451": {
        "wrappedProject": "MyProject.csproj"
    }
}
```

<a name="frameworks.bin"></a>
### bin
Type: Object

An object with a single property, `assembly`, whose value is the assembly path.

For example:

```json
"frameworks": {
    "netcoreapp1.0": {
        "bin": {
            "assembly" :"c:/otherProject/otherdll.dll"
        }
    }
}
```

<a name="frameworks.imports"></a>
### imports
Type: String

Specifies other framework profiles that this project is compatible with.

For example:

```json
"frameworks": {
    "netcoreapp1.0": {
        "imports": "portable-net45+win8"
    }
}
```

Will cause other packages targeting `portable-net45+win8` to be usable when targeting `netcoreapp1.0` with the current project.
