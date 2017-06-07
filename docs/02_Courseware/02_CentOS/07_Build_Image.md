## Overview
Now that we have our Dockerfile, let's build our image from it.

## Build the Docker Image
Once we have our Dockerfile, building the image is pretty simple.

From the command prompt, type `cd ~` to ensure you are in your home folder, then type the following:
```bash
docker build -t test/simpleweb .
```

This will build an image using `test/simpleweb` as the repository name. The period at the end specifies the path where Docker can find the Dockerfile.

Watch how Docker will step through our Dockerfile to build our image. Keep in mind while you watch this process that each step in our Dockerfile constitutes a layer in our image.  We'll see the results of this below.

## Check Your Images
From the command prompt, type the following:
```bash
docker images
```

You should see something similar to:
```bash
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
test/simpleweb      latest              d2c9a502fd30        3 minutes ago       469 MB
centos              latest              3bee3060bfc8        37 hours ago        193 MB
```

Our image has been built using the specified repository name. You'll also notice that the `centos` image has been downloaded.  This is because the build process required CentOS in order to build our image.  Now that our image has been built, you could delete the `centos` image if you wanted to.  Finally, when looking at the image sizes, you'll see that our image is 4 times larger due installation of Node.js, Git, and the other dependencies.  In the end, however, 500MB is still not that large.

## View Image History
What if we wanted to see how our image is constructed? Or, what if we wanted to see exactly how much disk space each layer of our image required? We could find this out by checking the image's history.

```bash
docker image history test/simpleweb
```

When you run the above command, you see each command along from our Dockerfile along with it's layer id and the space requirements, if any.

We've now built a custom image based on a Dockerfile. We can use our custom image to deploy containers locally. Or, we could upload our image to a central repository so that others could leverage our image's functionality.