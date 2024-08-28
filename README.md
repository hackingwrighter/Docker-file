
# Complet note - DOCKER

### what is docker:
docker is a containerization platform for developing,packaging,shipping,and running applications.it provides the ability to run an application in an isolated enviroment called a container.makes deployment and development efficient. 
![OIP](https://github.com/user-attachments/assets/298b4d3d-a9dd-4c05-b21a-acc64cb1ec99)

       To avoid ( this working on my mechine but not working on your mechine)
     

### what is a container:
A way to package an application with all the necessary dependencies and configuration .
it can be easily shared . makes deployment and development efficient

### Docker engine : INSTALL IT.
         Docker cli(we write the cmd here)
         Docker deamon
            ->dockerD (docker-D under stand the container-D code dockerD helps to call containerD by the help of API)
            ->containerD(it provide all tolls in which you can run the container)

Docker-File--------------------->Docker-Image------------------>Docker-container 

## first install Docker:

## Documentation

[https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/)

# PRACTICAl: REACT-DOCKER-PROJECT
```
FROM node:20-alpine
WORKDIR /myapp
COPY . .
RUN npm install
CMD ["npm","start"]


```

### CMD
| Command | Description |
| ------- | ----------- |
| `docker build .` | image build |
|`ducker images ls`|to know image creation,id|
|` docker run img-id`| run or start the container|
|` docker ps `| to know about container |
|` docker ps -a `| to know all container |
|` docker stop cont-name`| stop the container |
|` docker run -p 3000:3000 image-id`|start container outside the container in 3000 port number|
|` docker run -p 3001:3000 image-id`|start container outside the container in 3000 port number|
|` docker run -p 3002:3000 image-id`|start container outside the container in 3000 port number|
|` docker run -d -p 3000:3000 cont-Id` | detachmode is help to start the container in background |
|` docker rm container-id,cont-id,cont-id`|insted of container id you can give container  name|
|` docker run -d --rm -p 3001:3000 cont-Id`|when you finish then after cmd "docker stop" it will atomatically remove(container)|
|` docker stop cont-name`| help to stop container|
|` docker ps -a`|this cmd use after build images|
|` docker run -d --rm --name "my-app" -p 3004:3000 img-id `| help us to give the cont-name as per us|


### image-tagging:
when you run a container at that time a random name was assigned 
```
docker build -t my-app:01 .

docker build -t my-app:02 .

docker rmi my-app:02 

docker image ls

docker run -d --rm --name "mywebapp" -p 3001:3000 mywebapp:02
```

### try for nginx:

 ```
 docker pull nginx
docker image ls
docker run -p 8080:80 nginx:latest
```
# user interaction cmd:
python pogram:

print('pogram to sum two number')

num1=int(input('1st num'))

num2=int (input('2nd num'))

result= num1 + num2

print(f'sum of two num {result}')

### docker file:

FROM  python

WORKDIR  /myapp

COPY ./nameoffile.py .

CMD ["python", "nameoffile.py"]
```
CMD:
docker build .
docker image ls
docker run img-id  (don't run it)
docker run -it img-id  (for user input)
```

# DOCKER HUB CMD:
Create your docker-hub account and give the repo name and name space in my case it is 

 jashobant/webapp-deamo

 and login docker-hub in your terminal

 ## Terminal :
 build a image like jashobant/webapp-deamo  easy to push
 ```
 docker build -t jashobant/webapp-deamo:01 . 
 docker image ls 
 docker push jashobant/webapp-deamo:01 
 ```
 for pulling the img from docker-hub:
 ```
 docker pull jashobant/webapp-deamo:01
 ```

# How to rename image-name:
suppose a exist image like-> mywebapp:01

change to jashobant/webapp-deamo:01
```
docker tag mywebapp:01 jashobant/webapp-deamo:01
docker images
```

# docker volume

if we need some info from previous file exicution then we use volume to store info which is use for next exicution 
```
docker build .
docker images
docker run -it --rm --name myapp img-id
docker run -it --rm -v ${pwd}:file-name img-id
docker run -it --rm -v $(pwd):/app img-id
docker volume --help 
```
### bindmount(live update)
-->avoid to create repeted image

-->if you update on your local immediately it will change inside the docker-file

when you run a pogram which deal will data bases after exicution the data will fetch from local to container if you modify some thing inside the local system then that will not reflect:
```
docker run -v (python/some other file locatio):/(serverfile path which is present inside the docker-file) --rm img-id
```
# What is dockerignore:
if you want that some file is not going inside the docker images at that time you create a file named as ".dockerignore" and put on that
### .dockerignore  

# communication from/to Container-->
 
 ##################picture-3

 FROM python 

 WORKDIR /myapp

 COPY ./api_demo.py .

 RUN pip install requests //for import statement

 CMD ["python","api_demo.py"]


