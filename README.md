# Catesta

[![Minimum Supported PowerShell Version](https://img.shields.io/badge/PowerShell-5.1+-purple.svg)](https://github.com/PowerShell/PowerShell) [![PowerShell Gallery][psgallery-img]][psgallery-site] ![Cross Platform](https://img.shields.io/badge/platform-windows%20%7C%20macos%20%7C%20linux-lightgrey) [![License][license-badge]](LICENSE)

[psgallery-img]:   https://img.shields.io/powershellgallery/dt/Catesta.svg
[psgallery-site]:  https://www.powershellgallery.com/packages/Catesta
[psgallery-v1]:    https://www.powershellgallery.com/packages/Catesta/0.8.1
[license-badge]:   https://img.shields.io/github/license/techthoughts2/Catesta

<p align="center">
    <img src="./media/Catesta.PNG" alt="Catesta Logo" >
</p>

Branch | Windows - PowerShell | Windows - pwsh | Linux | MacOS
--- | --- | --- | --- | --- |
master | ![Build Status Windows PowerShell Master](https://github.com/techthoughts2/Catesta/workflows/Catesta-Windows-PowerShell/badge.svg?branch=master) | ![Build Status Windows pwsh Master](https://github.com/techthoughts2/Catesta/workflows/Catesta-Windows-pwsh/badge.svg?branch=master) | ![Build Status Linux Master](https://github.com/techthoughts2/Catesta/workflows/Catesta-Linux/badge.svg?branch=master) | ![Build Status MacOS Master](https://github.com/techthoughts2/Catesta/workflows/Catesta-MacOS/badge.svg?branch=master)
Enhancements | ![Build Status Windows PowerShell Enhancements](https://github.com/techthoughts2/Catesta/workflows/Catesta-Windows-PowerShell/badge.svg?branch=Enhancements) | ![Build Status Windows pwsh Enhancements](https://github.com/techthoughts2/Catesta/workflows/Catesta-Windows-pwsh/badge.svg?branch=Enhancements) | ![Build Status Linux Enhancements](https://github.com/techthoughts2/Catesta/workflows/Catesta-Linux/badge.svg?branch=Enhancements) | ![Build Status MacOS Enhancements](https://github.com/techthoughts2/Catesta/workflows/Catesta-MacOS/badge.svg?branch=Enhancements)



## Synopsis

Catesta is a PowerShell module project generator. It uses templates to rapidly scaffold test and build integration for a variety of CI/CD platforms.

## Description

Catesta enables you to quickly scaffold a PowerShell module project with proper formatting, test + build automation, CI/CD integration, with just one line of code.

* Catesta scaffolds an empty PowerShell module project that adheres to PowerShell community guidelines.
* It generates a few [Pester](https://github.com/pester/Pester) tests to get you started.
* It makes a [build file](https://github.com/nightroman/Invoke-Build) that analyzes your code for best practices and styling, runs Pester tests, creates PowerShell help, and combines your functions together to build your project for publication.
* It will create resources you need to trigger CI/CD builds for your module.
* When you commit your code to your chosen repository, the build(s) will run, and you can view the results.

## Why

Simplify the process of structuring your module so that you can focus on building a great PowerShell module instead of the layout and build requirements.

### Features

* [PowerShell module](https://docs.microsoft.com/powershell/scripting/developer/module/writing-a-windows-powershell-module) layout following PowerShell community practices
* *[Selection]* Required CI/CD integration files generated:
  * [AWS](https://aws.amazon.com/codebuild/)
  * [GitHub Actions](https://help.github.com/actions)
  * [Azure Pipelines](https://azure.microsoft.com/services/devops/)
  * [AppVeyor](https://www.appveyor.com/)
* *[Selection]* Build types for easy cross-platform testing
  * Windows PowerShell
  * Windows pwsh
  * Linux
  * MacOS
* [InvokeBuild](https://github.com/nightroman/Invoke-Build) tasks for validation / analysis / test / build automation
  * [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) code checks
    * *[Optional]* Code Style Enforcement (Stroustrup, OTBS, Allman)
  * [Pester](https://github.com/pester/Pester) Tests
    * Will run Unit / Infrastructure Tests if available
    * Generates Code Coverage Report
    * [Coverage Gutters](https://marketplace.visualstudio.com/items?itemName=ryanluker.vscode-coverage-gutters) support
  * *[Optional]* Create Help using [platyPS](https://github.com/PowerShell/platyPS)
    * Markdown-based help
    * External XML help file generation
  * Build and artifact creation
* *[Optional]* VSCode editor files
* *[Optional]* Helpful repository files
  * .gitignore
  * Project LICENSE (MIT / APACHE / GNU / ISC)
  * [Changelog](https://keepachangelog.com/en/1.0.0/)
  * GitHub community files:
    * Code of Conduct
    * Contributing guidelines
    * Templates
      * Issue Bug Report
      * Issue Feature Request
      * Pull Request

## Installation

```powershell
# Install Catesta from the PowerShell Gallery
Install-Module -Name Catesta -Repository PSGallery -Scope CurrentUser
```

## Quick start

```powershell
# Scaffolds a PowerShell module project for integration with AWS CodeBuild.
New-PowerShellProject -CICDChoice 'AWS' -DestinationPath c:\path\AWSProject

# Scaffolds a PowerShell module project for integration with GitHub Actions Workflows.
New-PowerShellProject -CICDChoice 'GitHubActions' -DestinationPath c:\path\GitHubActions

# Scaffolds a PowerShell module project for integration with Azure DevOps Pipelines.
New-PowerShellProject -CICDChoice 'Azure' -DestinationPath c:\path\AzurePipeline

# Scaffolds a PowerShell module project for integration with AppVeyor Projects.
New-PowerShellProject -CICDChoice 'AppVeyor' -DestinationPath c:\path\AppVeyor

# Scaffolds a basic PowerShell module project with no additional extras. You just get a basic PowerShell module construct.
New-PowerShellProject -CICDChoice 'ModuleOnly' -DestinationPath c:\path\ModuleOnly
```

## Getting Started

1. Use Catesta to scaffold your PowerShell project with your desired CI/CD platform and builds.
1. Write your module (the hardest part)
    * All build testing can be done locally by navigating to src and running ```Invoke-Build```
    * If using VSCode as your primary editor you can use tasks to perform various local actions
      * ```Press Ctrl+P, then type 'task test'```
1. Commit your project to desired repository that is integrated with your CI/CD platform. This will trigger the build actions.
1. Evaluate results of your builds and [display your README badges](https://github.com/techthoughts2/Catesta/blob/master/docs/Catesta-FAQ.md#how-do-i-display-the-badges-for-my-project) proudly!

Additional Catesta documentation that covers the process of CI/CD integration in depth:

* [Catesta - AWS Doc](docs/Catesta-AWS.md)
* [Catesta - GitHub Actions Doc](docs/Catesta-GHActions.md)
* [Catesta - Azure Pipelines Doc](docs/Catesta-Azure.md)
* [Catesta - GitHub AppVeyor Doc](docs/Catesta-AppVeyor.md)

## FAQ

**[Catesta - FAQ](docs/Catesta-FAQ.md)**

## Author

[Jake Morrison](https://twitter.com/JakeMorrison) - [https://techthoughts.info/](https://techthoughts.info/)

## Contributors

* [Andrew Pearce](https://twitter.com/austoonz)
* [Dave Kaylor](https://twitter.com/KaylorDave)

## Notes

## Changelog

Reference the [Changelog](.github/CHANGELOG.md)
