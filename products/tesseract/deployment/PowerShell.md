---
title: PowerShell CmdLets
excerpt: "Using the Tesseract PowerShell CmdLets for deployment"
---
# PowerShell Commands  

Users or DevOPs automation scripts can interact with a Tesseract instance using a set of CmdLets. 

The CmdLets are:

- Tesseract-Session
    -- Set-TesseractSession 
    -- Get-TesseractSession
- Type
    -- Compile-TesseractType
- Script
    -- Run-TesseractScript
- Commands
    -- Run-TesseractCommands 
- Boot strap
    -- Initialise-Tesseract
- Install
    -- Install-TesseractModule

Help
----
- **session** sessionName|default [bookmark|yyyy-MM-ddTHH:mm:ss]
- **sessions** -- list the sessons
- **bookmark** name [yyyy-MM-ddTHH:mm:ss] -- bookmark a timestamp for sessions. If no timestamp is provided UTC now is used
- **bookmarks** -- list the defined bookmarks
- **type** [fileName|fileIndex] [view]-- compile or view a type. List type files with no parameter
- **script** [fileName|fileIndex] [view] -- run or view a script. List script files with no parameter.
- **commands** [fileName|fileIndex] [view] -- run or views a set of commands from a file. List command files with no parameter
- **autocommit** true|false -- set whether transactions are autocommitted or not. Default is true
- **remote** true|false -- set whether this instance should do remote cache updates
security true|false -- enable or disable security
- **commit** -- commit current transaction
- **rollback** -- rollback current transaction
thread threadName|default -- switch to named thread
- **reset** -- resets state of application
- **bootstrap** -- delete the database and initialise with bootstarp records
- **install** assemblyFile typeName -- install an external type
- **clear** -- clear screen
- **dir** [directory] -- view or change script directory
- **database** name -- set the object database
- **about** -- display system information
- **quit** -- quit
