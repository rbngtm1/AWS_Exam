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
  * Periodically check the log files for errors in Cloudwatch or CloudTrial and send out notification through SNS.
  * Scheduled job to generate AWS resource usage reports based on certain tags.
  * A website with highly scalable backend layer which will persist data into RDS or DynamoDB.
#### AWSLambdaKinesisExecutionRole 
  * Grants permission for Amazon Kinesis Data Streams actions, and CloudWatch Logs actions. If you are writting a Lambda function to process Kinesis stream events you can attach this permission policy. 
     ex: 
     *             {
                   "Version": "2012-10-17"
                      "Statement": [
                           {
                              "Effect": "Allow",
                              "Action": [
                                   "kinesis:DescribeStream",
                                   "kinesis:GetRecords",
                                   "kinesis:GetShardIterator",
                                   "kinesis:ListStreams",
                                   "logs:CreateLogGroup",
                                   "logs:CreateLogStream",
                                   "logs:PutLogEvents"
                              ],
                              "Resource":"*"
                            }
                          ]
                    }
  
#### Note: Lambda execution role policy does not have access to create CloudWatch logs.       
#### When configuring AWS SQS as event source for AWS Lambda function, what is the maximum batch size supported by AWS SQS for ReceiveMessage call?
  * 10
#### Use constant values in Cloudwatch event triggered Lambda functions
![lambdatrigger](https://github.com/rbngtm1/solution_architect_associate/blob/master/lambdaimage.JPG)
#### Lambda Invoke API
  * You can invoke a Lambda function using a custom event through AWS Lambda's invoke API. Only the function's owner or another AWS account that the owner has granted permission can invoke the function. 
  * If you are using the versioning feature, you can invoke the specific function version by providing function version or alias name that is pointing to the function version using the Qualifier parameter in the request. If you don't provide the Qualifier parameter, the $Latest version of Lambda is invoked. 
  * If you use RequestResponse (synchronous) invocation option, the function will be invoked only once. 
  * If you use Event (asynchronous) invocation option, the function will be invoked at least once in response to an event and the function will be invoked at least once in response to the event and the fuction must be idempotent to handle this.
  * Lambda Invoke API is useful scenario if you are trying to migrate from on-premise to AWS while running processes based on triggers from other application. 
#### Amazon CloudFront events can be used to trigger function (AWS Lambda@edge)
![lambda@edge](https://github.com/rbngtm1/solution_architect_associate/blob/master/awslambda%40edge.JPG)
#### Do AWS lambda function remain available when I change my code or its configuration?
  * Yes. When you update a Lambda function, there will be a brief window of time, typically less than a minute, when requests could be served by either the old or new version of your function. 
#### Pull based services supported by Lambda
  * AWS Kinesis
  * Amazon DynamoDB
  * Amazon SQS
  
![lambdalimit](https://github.com/rbngtm1/solution_architect_associate/blob/master/lambdalimit.JPG)
#### If you have two account, add permission on the account which would trigger Lambda on another account through AWS CLI
  * You can also grant cross-account permissions using the function policy. For example, if a user-defined application and the Lambda function it invokes belong to the same AWS account, you don't need to grant explicit permissions. 
#### Lambda dead-letter queue pushes unprocessed events to:
  * AWS SQS
  * AWS SNS
#### Storing Sensitive Information
  * The lambda console provides encryption helpers that leverage AWS KMS to store sensitive information as Ciphertext.
  * The lambda console also provides decryption helper code to decrypt that information for use in your in Lambda function code. 
#### Which of the following actions are required by Lambda execution role in order to write the logs into AWS CloudWatch?
  * logs:CreateLogGroup
  * logs:CreateLogStream
  * logs:PutLogEvents
#### AWS/Lambda namespaces includes:
  * Invocations
  * Errors
  * Dead Letter Errors
  * Duration
  * Throttles
  * IteratorAge
  * ConcurrentExecutions
  * UnreservedConcurrentExecutions
#### If you are specified criteria like the code should not run if the version is $LATEST
  * getFunctionVersion from context object
    * If an alias is used to invoke the function, then getFunctionVersion will be the version the alias points to.
  * Use AWS_LAMBDA_FUNCTION_VERSION environment variable
#### Lambda invocation
![lambda_invocation](https://github.com/rbngtm1/solution_architect_associate/blob/master/lambdainvocation.JPG)
