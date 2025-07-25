
Docker run:

docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

Starts a container from specified image, optionally with a command + arguments.

If the image has a ENTRYPOINT in its dockerfile, the command is always what is specified in that, you can only add args.

If the image has a CMD at the end of its dockerfile, you can specify your own command to override it.

If it has neither, you can run any command you like - same as if there was a CMD.
