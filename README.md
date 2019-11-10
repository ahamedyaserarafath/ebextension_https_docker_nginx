# Ebextension - AWS Elastic Beanstalk - SSL
# Deploying the AWS Elastic Beanstalk in docker machine without using Load balancer
- [Introduction](#Introduction)
- [Installation and configuration](#Installation-and-configuration)

# Introduction
In this post, we will be using ebextenation to deploy the SSL in Elastic beanstalk without using Elastic Load balancer(ELB).
As I make sure bring the ssl with hassle free with a simple steps and simple configuration.

# Installation and configuration
Clone the project locally to your linux machine.

Copy the ebxtenstion as .ebxtenstion in your core code and upload a same in your AWS Elastic Beanstalk.

```
cp -r ebxtenstion <path_to_your_application>/.ebxtenstion
```

Add the below Environment properties in you Elastic Beanstalk.

