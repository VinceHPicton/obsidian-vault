
- What is the filesystem like in a specific container? 
	- It depends on which base image you use
    
- How can I check what the filesystem looks like?
	- You could run a command like `ls` when you build image, or you can use the above command: docker run -t -i image_name bash, BUT you’ll have to comment out an ENTRYPOINT or whatever if one exists that would try to run the container in another way.
    
- Why is it WORKDIR to /app for example?
	- This is just a best practice, it just separates your modifications to the container (from what the base image provides).
    
- What does WORKDIR /app do?
	- This is like cd for the rest of the Dockerfile, doesnt effect running container much, except if you bash into container you'll go to /app, if you use -v for example, it starts at the default root directory for that image (would be ../app in this example).
    
- Make an empty directory in a container? 
	- RUN mkdir my_dir_name
    
- How to make a container create a file in the host filesystem (the directories on the local computer running that container)? 
	- The only way is volumes
    
- What happens when you pass -v as an argument to docker run - Eg -v $(pwd):/app? 
	- Everything in the CONTAINERS path, (RIGHT of the colon), is overwritten by everything in the runners path (LEFT of colon). Remember that the containers path starts at the default root for the base image, NOT whatever you set as WORKDIR.
    