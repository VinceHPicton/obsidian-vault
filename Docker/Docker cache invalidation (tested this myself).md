Each line (instruction) of a [[3. Dockerfiles|Dockerfile]] creates an image "layer" which has a hash value, which is computed by hashing together:

- **The exact instruction text** (e.g., `RUN apt-get install ...`, `COPY file.txt /app/`)
- **The state of all files** referenced by that instruction (size, timestamps, and ultimately a checksum/hash of file contents in the build context)
- **The image state** from the layer before it (needed so that when it gets to that instruction when a previous instruction's hash has changed, docker will know to not use the cached version of this layer either - docker can just compare the )

You can see these hashes for yourself by running `docker inspect <image_name>`

So when it builds each layer:
1. Docker takes the current instruction, the files it references, and the hash of the previous layer.
2. It computes the hash for this step, using the above pieces of information 
		*note that computing a hash is an extremely fast operation, so this is very efficient*.
3. It looks in the cache: if a matching hash exists, it can reuse the layer (cache hit).
4. Only if there’s **no match** (cache miss) does Docker actually execute the instruction to build the layer.

**-- What is the take-away from all this? --**
Since the state of all files in each step is hashed, if you even change 1 character in 1 of the files involved in a Dockerfile instruction, the hash of the files referenced by that instruction will change, and this layer will then have a cache miss, causing all the subsequent layers to also cache miss, and the image to be rebuilt with your new code/file changes.

**This means docker's caching extremely sensitive, which is a good thing, because if you rebuild your image after changing your code, you shouldn't often need to force docker to invalidate the cache**


**If you want a concrete example**

Let’s say you have a Dockerfile:
```
FROM ubuntu:20.04

RUN apt-get update && apt-get install -y curl

COPY application-files /app/
```

- Step 2’s cache key = hash( `"RUN apt-get update && apt-get install -y curl"` + hash(from Step 1 image) )
- Step 3’s cache key = hash( `"COPY app.js /app/"` + hash of the files in application-file + the hash from Step 2 image)