Using S3 for a [[Static website]] is an option you can tick when creating a **bucket** on S3.
You would have 1 bucket for 1 website.

You will need an index.html file, and an error.html file which is shown for errors.

If you get a 403 (forbidden) error, make sure the bucket policy allows public reads.