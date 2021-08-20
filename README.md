# dockerfile-go-app
Simple go app and Dockerfile to build the image

## Build and run image
Build image by running \

`docker build -t simple-go -f simple-go-server .`

Verify Image in your local repository:

`docker images | grep -i simple-go`

Run image

`docker run -p 80:80 --name simple-go-container -d simple-go`

Verify that it's running

`docker ps | grep simple-go`

Curl the app

`curl localhost:80`

Check in browser http://localhost


## Build smaller image
There is a way to reduce the size of the image by 300Mb by building the binary file in an worker stage, and then transfering the binary application to "scratch" and running it from there.

### About scratch containers:
The scratch image is the smallest possible image for docker. Actually, by itself it is empty (in that it doesn't contain any folders or files) and is the starting point for building out images. In order to run binary files on a scratch image, your executables need to be statically compiled and self-contained.

source: https://support.snyk.io/hc/en-us/articles/360004012857-What-are-docker-scratch-based-images-

## Build the smaller image

`docker build -t smaller-go -f smaller-go-server .`