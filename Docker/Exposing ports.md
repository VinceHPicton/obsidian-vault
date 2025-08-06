This can be done by docker run with the -p HOST:CONTAINER argument, or via the "ports:" docker-compose.yml option.
Both are functionally the same.

[[EXPOSE]] in a Dockerfile is just metadata/documentation and does not actually expose any ports.