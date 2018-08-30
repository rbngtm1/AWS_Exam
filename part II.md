#### A consulting firm repeatedly builds large architecture for their customers using AWS resources from several AWS services including IAM, Amazon EC2, Amazon RDS, DynamoDB and Amazon VPC. The consultants have architecture diagrams for each of their architectures, and are frustrated that they cannot automatically create their resources. Service that will immediately benefit to the organization is:
  * AWS Cloudformation. 
    * Cloudformation enables consultants to user their architecture diagrams to construct CloudFormation templates. 
    * Cloudformation is a service that helps you model and set up your Amazon Web Service resources so that you can spend less time managing those resources and more time focusing on your application that run on AWS. You can create a template that describes all the AWS resources that you want (like Amazon EC2 instance or Amazon RDS DB instances), and AWS CloudFormation takes care of provisioning and configuring those resources for you. 
    
#### An organization hosts a multi-language website on AWS, which is served using CloudFront. Language is specified in the HTTP request as shown below:
  * http://d11111f8.cloudfront.net/main.html?language=de
  * http://d11111f8.cloudfront.net/main.html?language=en
  * http://d11111f8.cloudfront.net/main.html?language=es
  ****
  **how should AWS Cloudfront be configured to deliver cache data in the correct language?**
    * Based on query string parameter
