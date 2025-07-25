
`Docker image prune -a`
Remove all unused images, not just dangling

`Docker compose up –build`
(re)builds all images (if no changes will instantly complete due to caching layers) and start all containers.

`Docker compose up –build [container name]`
Only rebuilds and reattaches your specific container - saves time.

`docker run -t -i image_name /bin/bash` 
Connect to a container and look around via terminal
- (/bin/bash can just be bash or /bin/sh depending on what shell program is on the container and what's in $PATH, /bin/sh will nearly always exist)
- The -t just makes the shell more readable, like when you use ctrl+D it says exit instead of nothing
