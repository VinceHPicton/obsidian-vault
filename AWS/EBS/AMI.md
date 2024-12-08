Amazon Machine Image

This is a way to basically customize an EC2 instance so it starts off with exactly the software that you want on it.

AMIs are locked to a specific region but can be copied around

It's faster than having to manually redo your config every time, it just appears with what you want on it.

You can launch an EC2 from a few types of AMI:
- Public AMIs are provided by Amazon such as amazon linux, amazon windows etc
- Your own ones you created and have to maintain yourself
- AWS Marketplace AMIs these are created by 3rd party and might cost money

An AMI will include [[EBS snapshots|EBS snapshot]](s) but also has other components

**How you create AMIs:**
