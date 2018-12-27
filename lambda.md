#### Min memory = 128 MB, Max memory = 3008 MB
  * If the function reaches the maximum configuration, it will throw an error message (process exited before completing request)
#### Lambda function is set to run in a private VPC without NAT Gateway or VPC Endpoint.
  * Lambda function can run within a private VPC with the resources allocated inside the subnet provided during configuration.
#### For the lambda function to access S3 service endpoint from within private VPC, there should be a NAT Gateway or S3 VPC Endpoint configured in the route table associated within a subnet which was choosen during Lambda function setup. If not, the request would get timed out. 
