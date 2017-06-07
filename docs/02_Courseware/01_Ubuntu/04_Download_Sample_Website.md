## Overview
We've downloaded most of our dependencies.  In this step we will download a demo web site from GitHub, a remote source code repository.

## Clone the Website
'Cloning' is the method in which you download a remote repository to your local machine.  We are going to clone the demo web site to the default web hosting folder on our system.

From the command prompt, type the following:
```bash
sudo git clone https://github.com/AzureWorkshops/samples-simple-nodejs-website.git /var/www
```

You should see something similar to the following:
```bash
Cloning into '/var/www'...
remote: Counting objects: 9, done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 9 (delta 0), reused 6 (delta 0), pack-reused 0
Unpacking objects: 100% (9/9), done.
Checking connectivity... done.
```

The website source code has now been downloaded.