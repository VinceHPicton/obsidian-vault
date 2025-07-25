[CMD]([Dockerfile reference | Docker Docs](https://docs.docker.com/reference/dockerfile/#cmd)) specifies what command should be run when the container is started, however it **can** be overridden

**[ENTRYPOINT](https://docs.docker.com/reference/dockerfile/#entrypoint)** on the other hand, does also specify what command is run when the container is started, but it **CANNOT** be overridden.

Anything added to the end of the docker run command is appended to the command that ENTRYPOINT specified: eg from go-struct-generator below, the binary is always run when the container starts, and you just need to add the file path. More arguments than just 1 are allowed too, but exactly the number of arguments specified must be given in the run command.

`ENTRYPOINT ["../bin/go-struct-generator", "-file"]`

so **[ENTRYPOINT](https://docs.docker.com/reference/dockerfile/#entrypoint)** essentially turns the container into an executable, while CMD just sets a default command for if none is specified after `docker run` is run.

Also note:
ENTRYPOINT has two possible forms:
- The exec form, which is the preferred form:
` ENTRYPOINT ["path-to-executable", "param1", "param2", etc]`

- The shell form:
`ENTRYPOINT command param1 param2`


If you don't use either of these, docker will default to whatever the base image specified, and if that doesn't have anything either, you'll just get
`docker: Error response from daemon: no command specified`

