# What is a container?
* Layers of images
* Mostly **Linux Base Image**, because small in size
* Application image on top 

![image](https://user-images.githubusercontent.com/87442305/208294934-924397a9-7970-4515-886c-454a2bcf3e1c.png)

* A way to package application with all the necessary dependecies and configuration
* Portable artifects, easily shared and modes around
* makes development and deployment more efficient 

# Where do container live?
* Container Repository
* Private Repository
* Public repository for Docker (https://hub.docker.com/) 

# Advantage of containers
* own isolated environment 
* packaged with all needed configuration
* one command to install 
* run same app with 2 different version

## Before Containers
![image](https://user-images.githubusercontent.com/87442305/208294814-95b3b6a5-9c88-47df-82dc-d1d89d740733.png)


## After Containers 
![image](https://user-images.githubusercontent.com/87442305/208294798-ac3b2127-6131-4d6d-a216-cd5760955246.png)

# Create a image in docker environment 

### Pull image from docker hub (Eg. Postgress)

![image](https://user-images.githubusercontent.com/87442305/208295049-90879539-0c3e-4e6e-86f0-75a4789743b0.png)

run in terminal

![image](https://user-images.githubusercontent.com/87442305/208295146-5369ef1a-f94e-4dd2-b1b7-05a55842e6aa.png)

if you need specific version of the image (Eg. version 9.6 of postgres)

![image](https://user-images.githubusercontent.com/87442305/208295221-7e3c8cd0-daf7-4751-92cb-dbce3581bf1a.png)


