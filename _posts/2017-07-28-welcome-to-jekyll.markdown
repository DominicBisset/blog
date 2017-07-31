---
layout: post
title:  "Playing with Azure and Jekyll"
date:   2017-07-28 21:45:09 +0100
categories: Azure Jekyll Meta
---
This is a Hello World of sorts for a Jekyll-generated static site hosted on Azure

Mostly I'm following the [Publish a website with Jekyll and Github on Windows Azure][1] tutorial from [ANHELEDIR.NET][2].

It's not working so well now.  I can't get it to do build server-side.  Further investigation suggests the extension installer is failing.  

I'm now trying alternative installation instructions from [Deploying Jekyll to Windows Azure App Services][3].

The alternative approach hit different a different snag.  The build routine failed while trying to install `bundler`, ostentibly due to some code signing issue.  The solution is supposedly to install the latest `gem-update`.  But theoretically the build routine installs the latest version anyway, so it seems to hide the problem.

All my debugging is hampered by the fact that that, while I do have non-superuser console access through the azure portal to the server the code is running on, the console refuses to acknowledge the shift key.  It's a fairly fundamental flaw - want to cd to the `d:\local\temp` directory from the `d:\home\site\wwwroot` directory?  You can't do it absolutely because you can't type colons;  have fun going the long way around

``` cmd
cd ..\..\..\local\temp
```

The other issues are that the environement variables change between the deployment script and the console, and it takes three to five seconds for every pane to load so it takes ages to flit around investigating a problem.

So all in all I'm a bit sick of Azure. I've dropped the additional files that the [rimdev][3] tutorial asked for, and I'm jumping ship to GitHub pages.  Let's see how that goes.


[1]: https://gordon-breuer.de/azure/2016/03/01/Publish-a-website-with-Jekyll-and-Github-on-Windows-Azure.html
[2]: https://gordon-breuer.de/
[3]: https://rimdev.io/deploying-jekyll-to-windows-azure-app-services/