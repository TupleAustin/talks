Introduction to AWS Lambda
===

##### Running code without servers: [AWS Lambda](https://aws.amazon.com/lambda/)

###### Prepared by Alex Jestin Taylor ( [@alex-jestin-taylor](https://github.com/alex-jestin-taylor) )

---
# What is Lambda?

- **Essentially**: A code bundle at an API endpoint. 
- You simply upload your code bundle, specify some basic configuration information, and it sits there waiting to be invoked.
- AWS handles all the provisioning and handling of resources that are necessary to run your Lambda function.

---
# Why Lambda?

- There are no servers or infrastructure to manage.
- Lambda scales automatically with demand.
- Pay only for what you use in 100ms increments.

---
# $$$ - Lambda is Cheap!

- The first 1 million requests per month are free
- $0.20 per 1 million requests thereafter ($0.0000002 per request) for 128MB and 100ms.
- Some other costs may incur based on Lambda interacting with other AWS services.

---
# Creating a Lambda function

```bash
cd ~/Desktop
git clone https://github.com/TupleAustin/lambda-phantomjs.git
zip -r ../lambda.zip *
```
- Log in to the console: https://console.aws.amazon.com/lambda/
- 'Create a Lambda function'
- 'hello-world'
- 'Next'
- Give the function a name > assign a role > 'Allow' > 'Next' > 'Create function'