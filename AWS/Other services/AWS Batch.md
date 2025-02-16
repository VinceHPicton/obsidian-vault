Batch lets you run batch jobs on AWS.

What is a batch job? Well a batch job is a job that has a beginning and an end point - it's not running continuously like a web server.

- AWS Batch jobs are **Docker images** and they **run on ECS** which uses EC2 under the hood.
- They can also utilise a combination of spot-instances or normal EC2 to save money
- Batch handles assigning appropriate compute and memory to the jobs


It's different to Lambda because lambda
- Is restricted to only a few runtimes - node.js, Python
- Has a time limit, unlike a batch job which runs until complete
- Much more limited disk space, vs Batch which gets EBS volumes 
- Lambda is serverless, but Batch is running on EC2s
