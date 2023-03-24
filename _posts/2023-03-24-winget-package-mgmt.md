---
layout: post
title: Setup your Windows Dev machine with WinGet
date: 2023-03-24
categories:
- Automation
- Windows
- Security
tags:
- Automation
- Windows
- Security
permalink: "/winget-package-mgmt/"
share-img: "/assets/img/winget-package-img.png"
---
# Package Management
One of my favorite things about the linux operating system is their vast package management system that allows you to quickly get the applications you need, make sure their come from a trusted source, and make sure you can update these packages with a simple command such as apt-get update && apt-get upgrade.

Windows has had many attempts in this area including very successful 3rd party applications such as [Chocolately](https://chocolatey.org/). However where I had some issues with these is putting my complete trust in a 3rd party even though I believe they do the best they possibly can to maintain the security of the package manager.

For Mac OS, they have [homebrew](https://brew.sh/) - which they call the missing package manager. I find it to be quite helpful when I am leveraging my MacBook for automation and setup.

Definitely explore your options and see what is right for you. In this article I will be speaking mostly of my experience with WinGet.

# WinGet Setup

For WinGet you need to make sure you are running at least Windows 10. It may be installed by default. You can test this by opening up a PowerShell prompt and typing winget.

If it is not installed, follow the steps in the [Learn Microsoft article](https://learn.microsoft.com/en-us/windows/package-manager/winget/) to install WinGet on your computer to get you fully operational.

# Commands to get you started

For searching for new software, simply type

```
winget search <appname>
```

For example typing "winget search vscode" will get you all the applications relevant to VSCode.

To install the software on your dev workstation type

```
winget install <appname>
```

There are plenty of packages. There will be scenarios where there are missing packages and what you can do here is
- [Submit your own packages to the report](https://learn.microsoft.com/en-us/windows/package-manager/package/repository)

# Tips and tricks

## Export and Import

My favorite use of the tool is to get all the packages on my primary machine using the search and install commands above. Then take a snapshot and export the list to a JSON file.

```
winget export -o .\WinGetExport.json
```

This will capture all the packages you have installed on your machine, so when you create a new machine or VM you can restore the packages to the new machine to get you up and running in no time.

Here is the import command

```
winget import -i .\WinGetExport.json
```
  
## Update all packages

One feature I really love in this tool is the ability to update all my software at once, here is the quick command to do this on your dev workstation

```
winget upgrade --all
```
  
## Winget Settings

Another useful tip - is to check your winget settings, this is a config file where you can set the duration to auto-upgrade your applications on your dev workstation

```
winget settings
```

## Winget Security
One question that gets asked often is if Winget is secure ? The Windows Package Manager communtiy App Repository does mutliple automated scans of packages submitted during the submission process. This includes anti-virus and dynamic analysis. The community repository is also signed by Microsoft and is hosted on Microsoft Azure. I would say it is not full proof as you should always be cautious when installing new software from the internet. However it is infinitely better than clicking a random link or going to a random website to download software. Another tip is you can always check the file hash of the software or run the software through a tool such as [Virus Total](https://www.virustotal.com/gui/home/upload) to increase your confidence of the sofware you are installing from WinGet.
  
## In Closing
Hopefully this helped you get onboarded to help you automate your dev workstation. Please reach out if you have any questions. If you have any comments or feedback please reach out to me on [@udubnate on twitter](https://twitter.com/udubnate)