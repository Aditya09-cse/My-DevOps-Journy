# Take ubuntu as a base image
FROM ubuntu

# create a working Directory
WORKDIR	/app

#install curl
RUN apt-get update && apt-get install curl -y

# sets a default message to print
CMD ["echo" ,"Hello from my custom image!"] 
