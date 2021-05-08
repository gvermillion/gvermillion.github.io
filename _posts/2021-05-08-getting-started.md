---
layout: post
title:  "Getting Started with Python and Stellar"
categories: [howto]
tags: [stellar, jupyter, docker]
---

# Outline

- Docker Crash Course
- Deploy Dev Environment
- Jupyter Lab Crash Course + Test Environment

# Main

## Docker Crash Course

Briefly, Docker is a powerful tool that lets you create self-contained environments that can easily be passed around. Why is this so powerful though? Let me try to motivate this with a thought experiment:

 Consider what we are trying to do right now. I, on a machine running MacOS, am trying to help you, on a machine running an unknown OS, setup a local development environment with all necessary dependencies so you can use python to interact with Stellar. For this guide to be truly useful, I could do one of the following:
 
1. Write versions of the instructions for all possible operating systems, including those yet to be invented---a daunting task to put it mildly. 

1. Hand you a ready-to-go MacBook Pro with all of the dependencies installed, so you can immediately jump into developing. 

Both of these "solutions" are untenable for, what I hope are, obvious reasons."

### Enter Docker

What if, however, I could give you a ready-to-go *virtual machine* that you could run on whichever OS you choose? The only thing you would need is some interface layer that tells your machine how to run the virtual machine. That is **essentially** what Docker does:

- I can create a Docker <u>image</u> that includes all of the dependencies.
- I hand that image to you. 
- You build and run a <u>container</u> of said image.

When I was first learning about Docker, the metaphor that helped me conceptualize this was the following:

> Think of a Docker <u>image</u> loosely as a cake recipe. If I mail you the recipe for my favorite cake so you get to taste its glory, you can bake and eat your own at home (with your baked cake being the <u>container</u>).

### Install Docker

Assuming the above was enough to properly motivate you, head over to the extensive Docker [installation guides](https://docs.docker.com/get-docker/) and get Docker installed on your machine. 

I'll wait here!

## Deploy Dev Environment

Just a few more steps to go:

1 . To make things easier, I pre-built the image for you to pull down from [Docker hub](https://hub.docker.com/r/gvermillion/stellar_dev). To pull this image down, execute the following at command line:

```{sh}
docker pull gvermillion/stellar_dev
```

> NOTE: If you aren't sure how to access your command line, google, "Where is my command line?" or [click here](https://bfy.tw/QtKo).

This will initiate the image download, layer by layer, from Docker Hub. Download time will depend on your internet connection, but when it is done, you should see something like the following:

```{sh}
Status: Downloaded newer image for gvermillion/stellar_dev:latest
docker.io/gvermillion/stellar_dev:latest
```

2. Open the Docker Desktop client, and in the left bar, click on `Image`. You should see something like the following:

![Docker Desktop: Image Tab](https://www.dropbox.com/s/3uv70y5xttyj4zy/docker_desktop_01.png)

3. Hover over the `gvermillion/stellar_dev` image and click on `Run`:

![Docker Desktop: Run Container](/assets/resources/docker_desktop_02.png)

4. Expand the `Optional Settings` tab, add the following settings, and click `Run`:

![Docker Desktop: Optional Settings](/assets/resources/docker_desktop_03.png)

> NOTE: The "Volumes" section is optional, but it mounts a folder on your local machine to the virtual machine, so that if you stop the container, you still have access to the files on your local machine. 
>
> Be sure to choose paths that make sense for your machine, but the **container path must start with** `/home/jovyan/`

5. In the left bar, click on `Container/Apps`.

![Docker Desktop: Containers](docker_desktop_04.png)

6. Click on the `stellar` container to see the active logs. You need to copy the security token printed in the logs to be able to access the dev environment from your browser. It's printed in a few places; one is highlighted below:

![Docker Desktop: Token](/assets/resources/docker_desktop_05.png)

7. With the token copied, point your browser to [https://localhost:7117/lab](https://localhost:7117/lab) and paste the token when prompted. Voila! You know have a web-based dev environment (specifically an instance of Jupyter Lab.)

![Jupyter Lab: Landing](/assets/resources/jupyter_lab_01.png)

## Jupyter Lab Crash Course + Test Environment

I could write ad nauseam about Jupyter Lab, but suffice it to say that it is an interactive development environment (IDE) that can run all types of code. As you can see from the screenshot above, this version of Jupyter Lab can run Python, Julia, and R code. (You can also install different *kernels* to run other languages, like C++.)

The goal of this article, though, is to get you access to a Python environment with the `stellar-sdk` dependency, so we will skip a guided tour of Jupyter Lab. (BUT, I encourage you to play around inside Jupyter Lab and discover more features for yourself.)

1. Under `Console`, click on `Python 3`, which will open up an interactive Python console.

![Jupyter Lab: Console](/assets/resources/jupyter_lab_02.png)

2. In the text bar at the bottom of the console, type the following (`Enter/Return` will give you a link break): 

```{python}
import stellar_sdk
stellar_sdk.__version__
```

3. Hit `Shift+Enter/Return` to submit the code. You should see `3.3.1` returned:

![Jupyter Lab: Console 2](/assets/resources/jupyter_lab_03.png)

Congrats! You are now ready to start developing Python code using `stellar_sdk`!

## Support / Further Help

If you found this guide helpful, consider tossing a XLM or two my way:

```{sh}
GDPE3KZPQQ2QEJPYQQQQXCLYKVFAWLYQ3T6HJTRS5LER3BVP2PATIPME
```

If you need further help, [submit an issue](https://github.com/gvermillion/gvermillion.github.io/issues) on GitHub, and I'll try to help you out!


```python

```
