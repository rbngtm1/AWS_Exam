#### Min memory = 128 MB, Max memory = 3008 MB, can update in 64 MB increment
  * If the function reaches the maximum configuration, it will throw an error message (process exited before completing request)
#### Lambda function is set to run in a private VPC without NAT Gateway or VPC Endpoint.
  * Lambda function can run within a private VPC with the resources allocated inside the subnet provided during configuration.
#### For the lambda function to access S3 service endpoint from within private VPC, there should be a NAT Gateway or S3 VPC Endpoint configured in the route table associated within a subnet which was choosen during Lambda function setup. If not, the request would get timed out. 
#### Services not supported by Lambda:
  * AWS CodePipeline
  * AWS OpsWorks
#### AWS Lambda Dead Letter Queues builds upon the concept by enabling Lambda functions to be configured with an SQS queue or SNS topic as a destination to which the Lambda service can send information about an asynchronous request when processing fails.
#### AWS Lambda runs your function code within a VPC by default. However, to enable your Lambda function to access resources inside your private VPC, you must provide additional VPC-specific configuration information that includes VPC subnet IDs and security group IDs. AWS Lambda uses this information to set up elastic network interfaces (ENIs) that enable your function to connect securely to other resources within your private VPC.
  * If you get connection failed while connecting RDS from lambda, may be :
    * Lambda function is running in "no VPC" network mode.
    * Lambda is running in same VPC as RDS, but RDS instance security group is not allowing connections from Lambda subnet range. 
#### Customers responsibility with respect to AWS Lambda service?
  * Lambda function code.
  * Providing accesss to AWS resources which triggers Lambda function.
#### Supported language
  * Node.js, Java, Go, C#, and Python
#### Ephemeral disk capacity("/tmp" space) is 512 MB. Potential use case of Lambda is:
  * Download S3 bucket objects of size varying between 500 MB - 2GB to a Lambda Ephemeral disk or temp location, read and analyze them for key words and add the key words to the metadata of file object for search purposes.
