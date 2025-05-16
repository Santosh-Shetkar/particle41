## Code to initialize and use a remote Terraform backend (S3 and DynamoDB) for state and locking instead of a local .tfstate file.

I completed this task differently by using the new S3 bucket locking instead of the old method of using DynamoDB for Terraform state locking.

You can check it in Task2-> Part1
