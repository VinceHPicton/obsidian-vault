A key-value pair which exists outside your code, as part of the operating system or runtime environment, and can be accessed by the program during execution. The really defining feature is **environment variables are for things that change per environment (dev/staging/prod).**

They exist so that configuration and secrets can be kept separate from the code, for example meaning you don't have to put API keys in the code

It is slightly different from [[config]] because config is for "[[business logic]] settings" - things like expectedNumberOfColumnsPerCSVLine would be in config, because this **wouldn't change between environments** 

Some examples:
- API_KEY
- DATABASE_URL
- JWT_SECRET
- AWS_S3_BUCKET_ADDRESS
- FEATURE_X_ENABLED