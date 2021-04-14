---
title: PowerShell CmdLets
excerpt: "Using the Tesseract PowerShell CmdLets for deployment"
---
# PowerShell Commands  

Users or DevOPs automation scripts can interact with a Tesseract instance using a set of CmdLets. 

Example:
```
$env = get-environment -URL https://dev1.tesseract.net

or
$appSettings = .\appsettings.json
$settings = get-content $appSettings | convertFrom-json -AsHashTable
$env = get-environment -settings $settings

$t1 = build-type $env PersistedType1_v1.cs
```

The CmdLets are:

- ```Get-Environment```: Get a connection to a Tesseract environment - directly or via URL
    - Syntax:
        - ```Get-Environment -URL <string>```
        - ```Get-Environment [-SettingsFile <string>] [-TypeAssemblyPath <string>] [-DefaultSessionId <string>] [etc.]```
    - Returns: TesseractConnection
- ```Build-Type```: compile a type file into a type assembly and update dependent type assemblies
    - Syntax:
        -  ```Build-Type [[-Environment] <TesseractConnection>] <string> [-File] <string>```
    - Returns: TypeAssembly definition or compile Exception?
- ```Install-Type```: install a library containing type definitions and create a type assembly for the primary type
    - Syntax:
        - ```Install-Type -URL <string> [-File] <string> -[Type] <string>```
        - ```Install-Type -Database <string> [-File] <string> -[Type] <string>```
    - Returns: Type Assembly definition or install Exception?
- ```Invoke-Script```: run a script
    - Syntax:
        - ```Install-Types -URL <string> [-Script] <string> [-Build] [-View]```
        - ```Install-Types -Database <string> [-Script] <string> [-Build] [-View]```
    - Returns: ?
- ```Set-Session```: switches to a session
    - Syntax:
        - ```Set-Session [[-Environment] <TesseractConnection>] [-Name] <string>|default ```
    - Returns: Session definition
- ```New-Session```: switches to or creates a new session? Different commands?
    - Syntax:
        - ```New-Session [[-Environment] <TesseractConnection>] [-Name] <string> [[-Timestamp] <date time>] [-switch]```
    - Returns: Session definition
- ```Get-Session```: get details about a session or a list of sessions
    - Syntax:
        - ```Get-Session [[-Environment] <TesseractConnection>] [-Name] <string>|default```
    - Returns: List of Session definitions
- ```Reset-Environment```: bootstrap a Tesseract database
    - Syntax:
        - ```Reset-Environment [[-Environment] <TesseractConnection>]```
    - Returns: ?
- ```Complete-Transaction```: commit a Tesseract Transaction
    - Syntax:
        - ```Complete-Tesseract```
    - Returns: in verbose mode a list of committed items?
- ```Undo-Transaction```: rollback a Tesseract Transaction
    - Syntax:
        - ```Undo-Tesseract```
    - Returns: in verbose mode a list of rolled back items?

- About: this is information about environment, i.e. ```$env.About()```

### Example interaction

![PowerShell Interaction](../images/PowerShellInteraction.png)

### Transactions script options

1. Explicit commands for complete/undo transaction

```
...
$env = get-environment -settings $settings -autoCommit=false

$t1 = build-type $env PersistedType1_v1.cs

complete-transation
```

2. Have -commit / -rollback parameter for set-environment cmdlet

```
...
$env = get-environment -settings $settings 

set-environment -autoCommit = false

$t1 = build-type $env PersistedType1_v1.cs

set-environment -commit
```
Options 1 is better as verbs convey action and more transparent to user