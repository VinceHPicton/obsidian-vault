The build context is basically a directory on your host computer you want to give docker a copy of, so you can take things from it and put them into your image.
Docker literally sends a copy of the build context directory and everything inside it to its build process, so obviously, it can't access any files or folders from your machine that weren't inside the build context.

For example: So if you've used ~/myproject/dockerstuff as your build context (with a command like `docker build -t test ~/myproject/dockerstuff`), but your code is in ~/main.go and then you try to COPY it in with your Dockerfile with a command like `COPY "../../main.go" .` you'll find you're not able to - it wasn't copied into the build process.

Also, any file paths you pass to the Dockerfile which refer to a location on your computer (like the first arg in COPY), are relative to the build context. So if you try to do `COPY ./cmd/main.go .` it's going to assume there is a folder called cmd with a file called main.go, in the build context, and it'll fail the build if it doesn't find it there.


The build context is most often going to be the directory you're currently in, which is why you'll see `docker build -t myimage .` most often...
The `.` means "where I am right now" or "present working directory"