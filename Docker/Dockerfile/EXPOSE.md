This is **just metadata** which conveys what ports the containerized application is **expected** to listed on while running.

EXPOSE 80
This means: "The application inside this container will listen on port 80."

It's just documentation and is not even enforced by docker, but obviously a wrong EXPOSE statement makes it confusing for whoever uses your image.

You can use `docker image inspect` on an image, and it'll tell you what the Dockerfile says should be EXPOSED inside the container - ie you still need to choose a port on the host to map to that exposed inner port.