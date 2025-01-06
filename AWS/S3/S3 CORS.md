Learn about [[CORS]]

If we want to allow a client makes a cross-origin request to our S3 bucket, we must enable the bucket to respond with the correct CORS headers.

An example of this might be a static website at http://website-bucket/index.html requests an image from http://assets-bucket/home-image.png 

You could set up the assets bucket to reply with `Access-Control-Allow-Origin: "*"` (any) to allow this for example.