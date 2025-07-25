
ARG allows us to define variables that are available during the build process, while ENV specifies environment variables that will be set in the running container.

[https://vsupalov.com/docker-arg-vs-env/#:~:text=ENV%20is%20mainly%20meant%20to,after%20the%20image%20is%20built](https://vsupalov.com/docker-arg-vs-env/#:~:text=ENV%20is%20mainly%20meant%20to,after%20the%20image%20is%20built).

## ENV is for future-running containers. ARG for building your Docker image.

ENV is mainly meant to provide default values for your future environment variables

ARG values are not available after the image is built

![[ARG and ENV.png]]