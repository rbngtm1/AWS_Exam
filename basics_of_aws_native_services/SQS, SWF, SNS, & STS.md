# SQS
#### About SQS
  * Fully-managed queuing service
  * Loose coupling - high availability, scalibility and reliability
  * Uses multiple redundant AZs within a region
  * Integrated with IAM
  * PCI DSS compliant (can transmit merchant/ card data): payment card industry data security standard
  * Multiple producers and consumers can interact with SQS at the same time
  * 1 million requests/mont is free
  * Message size = 256 KB
  * supports JSON, XML, unformatted text
  * at-least-once delivery = more than one copy can be delivered.
#### Types(SQS)
  * Standard(default)
  * FIFO 
    * Exactly once processing
    * Limited to 300 TPS(transactions per sec)
#### Visiblity Timeout
  * Default is 30 sec
  * max is 12 hrs
#### SQS guide
  * When a customer receives and processes a message from a queue, the message remains in the queue. AWS SQS doesn't automatically delete the message.
  * SQS is a distributed system, there's no gurantee that the customer actually receives the message( for ex, due to connectivity issue, or due to an issue in the consumer application). Thus, the customer must delete the message from the queue after receiving and processing it. 
  * Immediately after a message is received, it remains in the queue. To prevent other consumers from processing the message again, AWS SQS sets a visibility timeout, a period of time during which AWS SQS prevents other consumers from receiving and processing the message. 
  * The default visibility timeout for a message is 30 seconds. The minimum is 0 seconds. The maximum is 12 hours.
  * Can be used with autoscaling groups
  * You can create a priority queue (process differently for premium and standard members)
  * Producer =>SNS Topic =>Order Queue/Audit Queue
  * can send/receive/delete max 10 message in a request (batch versus single)
  * Message retention period ( 1 minute to 14 days), default is 4 days
  * Delay queues let you postpone the delivery of new message in a queue for the specific number of seconds
  * A dead letter queue is queue that source queues can target for messages that can't be processed (consumed) successfully.

#### AWS SQS Long Polling
  * Short polling(default) returns immediately even if there are no message in the queue.
  * Long polling eliminates false empty responses by quering all (rather than a limited number) of the servers.
  * Long polling returns message as soon as any message becomes available.
  * Change ReceiveMessageWaittimeSeconds(0-20 seconds max)
  * can help avoid buring of CPU cycles (forex: when using EC2 to process your message)
  * long polling helps reduce the cost of SQS by eliminating the number of empty responses (when there are no message available for a ReceiveMessage request) and false empty responses (when messages are available but aren't included in a response). 
  * You can enable long polling for a new or existing queue using the AWS Management Console or AWS SDK for Java
```console
Benefits of Long Polling
    - Eliminate empty responses by allowing Amazon SQS to wait until a message is available in a queue before sending a response
    - Eliminate false empty responses by quering all
    - Return message as soon as they become available
```
#### Note: You can confirm that a queue is empty when you perform a long poll and the ApproximateNumberOfMessagesDelayed, ApproximateNumberOfMessagesNotVisible, and ApproximateNumberOfMessagesVisible metrics are equal to 0 at least 1 minute after the producers stop sending messages (when the queue metadata reaches eventual consistency). For more information, see Available CloudWatch Metrics for Amazon SQS.
#### AWS SQS Batch Actions
  * To reduce costs or manipulate up to 10 messages with a single action, you can use the following actions:
    * SendMessageBatch
    * DeleteMessageBatch
    * ChangeMessageVisibilityBatch
  * You can take advantage of batch functionality using the Query API, or an AWS SDK that supports the AWS SQS batch actions.
#### SQS facts
  * To select the message to delete, use the ReceiptHandle of the message (not the MessageID which you receive when you send the message)
  * You can use dead letter queues to isolate messages that can't be processed for later analysis.
  * SQS doesn't encrypt messages by default.
# SWF
#### Programming language SDK's available for SWF
  * Java, Ruby, .NET and PHP
####  Can I use AWS Identity and Access Management (IAM) to manage access to Amazon SWF? 
  * Yes. You can grant IAM users permission to access Amazon SWF. IAM users can only access the SWF domains and APIs that you specify.
#### Maximum number of SWF domains allowed in an AWS account is 100
  * You can have a maximum of 10,000 workflow and activity types (in total) that are either registered or depreciated in each domain. 
  * You can have a maximum of 100 Amazon SWF domains(including registered and depreciated domains) in your AWS account. 
  * gurantees delivery order of message/tasks.
#### How long can workflow executions run
  * Each workflow execution can run for a maximum of 1 year. Each workflow execution history can grow up to 25,000 events.
#### In SWF what are the containers called for segregating application resources.
  * Domains
    * In SWF, you define logical containers called domains for your application resources. Domains can only be created at the level of your AWS account and may not be nested
#### Developing Deciders in Amazon SWF
  * A decider is an implementation of the **coordination logic** of your workflow type that runs during the execution of your workflow. You can run multiple deciders for a single workflow type.
#### True about SWF
  * Human can perform an activity task, but not decision task. 
#### Some core benefits of SWF
  * One of the major use case of SWF is video encoding
  * Centralize the coordination of steps in the application
  * Automate the workflow that include human tasks
  * Manage the flow of work between application components
  * Integrate a range of programs and components 
  * help developers use asynchronous programming in the development of their applications
# STS
#### STS facts
  * STS enables you to request temporary, limited-privilege credentials.
  * STS enables users to assume role
  * STS generates Federated Credentials for IAM users
  * IAM user used to generate Federal User credentials does not have access on S3 bucket
  * AWS allows federated user's request only when both the attached policy and the IAM user policy explicitly allow the federated user to perform the requested action. 
#### STS AssumeRoleWithSAML
  * Returns a set of temporary security credentials for users who have been authenticated via a SAML authentication response. 
  * The temporary security credentials returned by this operation consist of an access key ID, a secret access key, and a security token.
  * By default, the temporary security credentials created by AssumeRoleWithSAML last for one hour. However, you can use the optional DurationSeconds parameter to specify the duration of your session.
# SNS
 * The various SNS endpoints for northern virginia:
    * US-East-1 (Virginia): http://sns.us-east-1.amazonaws.com 
#### What are appropriate ways for you to provide timely, device-specific instructions to end users when annoncing this downtime?
  * Send a single message, but customize the text in the SNS message field so that each device gets only the information that is appropriate for them.
#### What is the format of an Amazon SNS topic?
  * Topic names are limited to 256 characters. Alphanumeric characters plus hyphens (-) and underscores (_) are allowed. Topic names must be unique within an AWS account. After you delete a topic, you can reuse the topic name.
  * When a topic is created, Amazon SNS will assign a unique ARN (Amazon Resource Name) to the topic
  * The following is the ARN for a topic named “mytopic” created by a user with the AWS account ID “123456789012” and hosted in the US East region:

arn:aws:sns:us-east-1:1234567890123456:mytopic 
#### How long will subscription requests remain pending, while waiting to be confirmed?
  * Token included in the confirmation message sent to end-points on a subscription request are valid for 3 days.
#### Can a message be deleted after being published?
  * No, once a message has been successfully published to a topic, it cannot be recalled.
#### Does Amazon SNS provide at-least-once message delivery to Amazon SQS queue?
  * Yes, Amazon SNS gurantees that each message is delivered to Amazon SQS at least once. 
#### Protocols for AWS SNS
  * HTTP
  * HTTPS
  * Email
  * Email-JSON
  * Amazon SQS
  * Application
  * AWS Lambda
  * SMS
#### SNS Message Filtering
  * to exclude message for someone in group
#### SNS Message Attribute Items and Validation
  * Name: A-Z, a-z, 0-9,underscore(_),hyphen(-), and periods(.). The name must not start or end with period. It can be 256 character long
  * Type: Data types are String, String.Array, Number, and Binary. the data is case-sensative and can be 256 bytes long
  * Value
  * message size restriction: 256 KB
  * Name, type, and value can't be empty or null. 
  
