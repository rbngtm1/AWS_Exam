#### Min memory = 128 MB, Max memory = 3008 MB, can update in 64 MB increment
  * If the function reaches the maximum configuration, it will throw an error message (process exited before completing request)
#### Lambda function is set to run in a private VPC without NAT Gateway or VPC Endpoint.
  * Lambda function can run within a private VPC with the resources allocated inside the subnet provided during configuration.
#### For the lambda function to access S3 service endpoint from within private VPC, there should be a NAT Gateway or S3 VPC Endpoint configured in the route table associated within a subnet which was choosen during Lambda function setup. If not, the request would get timed out. 
#### Services not supported by Lambda:
  * AWS CodePipeline
  * AWS OpsWorks
#### AWS Lambda Dead Letter Queues builds upon the concept by enabling Lambda functions to be configured with an SQS queue or SNS topic as a destination to which the Lambda service can send information about an asynchronous request when processing fails.
#### 
