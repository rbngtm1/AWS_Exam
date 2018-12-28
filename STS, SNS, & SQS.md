#### SQS guide
  * When a customer receives and processes a message from a queue, the message remains in the queue. AWS SQS doesn't automatically delete the message.
  * SQS is a distributed system, there's no gurantee that the customer actually receives the message( for ex, due to connectivity issue, or due to an issue in the consumer application). Thus, the customer must delete the message from the queue after receiving and processing it. 
  * Immediately after a message is received, it remains in the queue. To prevent other consumers from processing the message again, AWS SQS sets a visibility timeout, a period of time during which AWS SQS prevents other consumers from receiving and processing the message. 
  * The default visibility timeout for a message is 30 seconds. The minimum is 0 seconds. The maximum is 12 hours.
#### AWS SQS Long Polling
  * long polling helps reduce the cost of SQS by eliminating the number of empty responses (when there are no message available for a ReceiveMessage request) and false empty responses (when messages are available but aren't included in a response). 
  * You can enable long polling for a new or existing queue using the AWS Management Console or AWS SDK for Java
```console
Benefits of Long Polling
    - Eliminate empty responses by allowing Amazon SQS to wait until a message is available in a queue 
```
