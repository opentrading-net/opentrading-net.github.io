---
title: PowerShell Tests
excerpt: "Pester and Tesseract CmdLets"
---
# Pester Tests


Example:
```
param ($env)

Describe 'Compile Test Types' {

  It 'Compile PersistedType1' {
    $t1 = build-type $env ".\PersistedType1_v1.cs"   
    $t1 | Should -Not -BeNullOrEmpty  
  }
}
```



## Running the Test Suite

```
.\Run.Tests.ps1
```

Or to run a specific test

```
invoke-pester .\Run.Tests.ps1 -name 'Run.CompileAndCreatePersistedType2Objects'
```

