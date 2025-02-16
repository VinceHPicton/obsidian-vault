SSM = AWS systems manager
Secure storage of configuration and secrets, with optional seamless encryption of data with KMS

You can setup a **parameter store hierarchy** to give permissions to subsets of parameters. 
Eg: /my-app/dev/db-url

**The two types**

**Standard**
- 10k params
- 4KB max size
- Free

**Advanced**
- 100k params
- 8kb size
- not free
- Can have parameter policies - like TTL