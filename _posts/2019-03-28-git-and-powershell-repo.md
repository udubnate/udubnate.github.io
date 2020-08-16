---
layout: post
title: GIT and PowerShell Repo
date: 2019-03-28 04:48:54.000000000 -07:00
categories:
- PowerShell
tags:
- Code
- GIT
- PowerShell
permalink: "/git-and-powershell-repo/"
---
I started a PowerShell repository in my GitHub called [Windows-Server-Admin](https://github.com/udubnate/Windows-Server-Admin). This will be where I am putting some of the code that I have leveraged to help me administrate on Windows Server. I wanted to share some of the scripts and tools I have found to be useful. (If you are new to GIT then I recommend you check out my friend's blog post -   
[https://thomasrayner.ca/first-git-commands/](https://thomasrayner.ca/first-git-commands/) )

The first script I will discuss is Get-FileSize.ps1 . I got the idea from a spiceworks [article](https://community.spiceworks.com/topic/1971559-getting-folder-subfolder-file-list-and-sizes)that had a majority of the code already written. I packaged it up in a function, tweaked it, and added comments for support.

The idea of the function is it allows you to get directory sizes of child folders without having to have a 3rd party tool deployed to your server. This helps when you have to figure out how to clean up disk space or possibly who is using the most space (such as UserProfiles.)

**Pro Tip** : I would advise you before running the script to read through it all to make sure you understand it. This is a overall general best practice for security as you want to make sure anything you download from the internet won't impact your computer. Sure you can trust me, but please verify as a best practice.

Here is a link to the script -   
[https://github.com/udubnate/Windows-Server-Admin/blob/master/Get-FileSize.ps1](https://github.com/udubnate/Windows-Server-Admin/blob/master/Get-FileSize.ps1) (click the RAW button to get only the script)

Here is an example of how to run the script on your system. Open up PowerShell, right-click and run as Administrator if you run into issues with hidden folders or folders that you need elevated access to see. Copy and paste the script into the PowerShell console.

``` powershell
PS> Get-FileSize -startFolder "c:\users"

Output:

C:\users\defaultuser0 -- 44.21 MB
C:\users\nate -- 226,860.85 MB
C:\users\Public -- 13,060.06 MB
```

Wow, I really need to clean up some files in my profile. I could then run the script again in the "c:\users\nate" folder for example.

This is a good way of doing some quick investigation and look for those pesky big folders or big files that are hiding.

I hope you enjoyed this post, please let me know if you enjoyed this sort of content, this feedback will help me determine what to post in the future.

