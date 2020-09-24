# terraform-aws-sqs-cloudwatch-alarms
Terraform module for creating alarms for SQS and notifying endpoints


## Usage

```hcl
module "user_queue" {
  source  = "terraform-aws-modules/sqs/aws"
  version = "~> 2.0"
  name = "user"
  tags = {
    Service     = "user"
    Environment = "dev"
  }
}
```

## Examples

* [SQS queues with server-side encryption (SSE) using KMS and without SSE](https://github.com/terraform-aws-modules/terraform-aws-sqs/tree/master/examples/complete-sqs)

## Conditional creation

Sometimes you need to have a way to create SQS queue conditionally but Terraform does not allow to use `count` inside `module` block, so the solution is to specify argument `create`.

```hcl
# This SQS queue will not be created
module "user_queue" {
  source  = "terraform-aws-modules/sqs/aws"
  version = "~> 2.0"
  create = false
  # ... omitted
}
```