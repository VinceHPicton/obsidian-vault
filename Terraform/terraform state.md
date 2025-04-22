You should use an s3 bucket and a DynamoDB table for this.

**Read the comment: Essential the hash_key is exactly this**
```
resource "aws_s3_bucket_versioning" "enabled" {
  bucket = aws_s3_bucket.terraform_state.id
  versioning_configuration {
    status = "Enabled"
  }
}

resource "aws_dynamodb_table" "terraform_locks" {
  name         = "terraform-up-and-running-locks"
  billing_mode = "PAY_PER_REQUEST"
  
  # Essential the hash_key is exactly this
  hash_key     = "LockID"

  attribute {
    name = "LockID"
    type = "S"
  }
}
```

You should also encrypt the bucket, and deny all public access, I've left this out for clarity on what is actually needed.

This is config for terraform itself that'll tell it to use the bucket as its backend
```
terraform {
  backend "s3" {
    bucket         = "terraform-up-and-running-state-ch3-vincepicton31032025"
    key            = "global/s3/terraform.tfstate"
    region         = "us-east-2"

    dynamodb_table = "terraform-up-and-running-locks"
    encrypt        = true
  }
}

```