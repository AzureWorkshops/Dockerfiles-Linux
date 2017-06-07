## Overview
Our custom image has now been created and is currently sitting in our local repository. Let's instantiate a container based on that image.

## Start a Container
To start a container from our image is very simple.  The only thing we need to remember is exposing the internal port to the host.

```bash
docker run -d -p 8080:8080 --name 'web_8080' test/simpleweb 
docker run -d -p 8081:8080 --name 'web_8081' test/simpleweb
docker run -d -p 8082:8080 --name 'web_8082' test/simpleweb
```

We've started 3 separated instances of our web server. We've bound the web server's internal port 8080 to three host ports (e.g 8080-8082). We've also supplied meaningful names to our containers.  We can reference those containers by the names we've specified for easier management.  For example, we can restart or stop a container using it's name instead of the container id.

Check the running images:
```bash
docker ps
```

You should see something like the following:
```bash
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS                    NAMES
3d1929c8e1b5        test/simpleweb      "/bin/sh -c 'node ..."   3 seconds ago        Up 2 seconds        0.0.0.0:8082->8080/tcp   web_8082
323a65fa5143        test/simpleweb      "/bin/sh -c 'node ..."   11 seconds ago       Up 10 seconds       0.0.0.0:8081->8080/tcp   web_8081
7d4fee5c8f89        test/simpleweb      "/bin/sh -c 'node ..."   About a minute ago   Up 59 seconds       0.0.0.0:8080->8080/tcp   web_8080
```

Notice that all three containers are running, but, as we've specified, are bound to different ports and have custom names.

For practice, restart `web_8081`:
```bash
docker restart web_8081
```

Executing the command, may take a second. After it completes, check the running images again. You should now see that the uptime for `web_8081` is less than the other two containers.

We are left with successfully creating three container instances running our custom image.