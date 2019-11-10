# Ebextension - AWS Elastic Beanstalk - SSL
# Deploying the AWS Elastic Beanstalk in docker machine without using Load balancer
- [Introduction](#Introduction)
- [Installation and configuration](#Installation-and-configuration)
- [Flow](#Flow)

# Introduction
In this post, we will be using Ebextension to deploy the SSL in Elastic beanstalk without using Elastic Load balancer(ELB).
As I make sure bring the ssl with hassle free with a simple steps and simple configuration.

# Installation and configuration
Clone the project locally to your linux machine.

Copy the ebxtenstion as .ebxtenstion in your core code and upload a same in your AWS Elastic Beanstalk.

```
cp -r ebxtenstion <path_to_your_application>/.ebxtenstion
```

Add the below Environment properties in you Elastic Beanstalk.

| key | value |
| ------------- | ------------- |
| cert_path              | <download_link>        |
| key_path               | <download_link>        |
| location_cert_key      | /mnt/cert/    |

# Flow

1. Create a https nginx configuration with the as /etc/nginx/sites-available/https_server.conf
2. Delete the ***location_cert_key*** directory and create the same.
3. Download the ***cert_path*** and ***key_path***.
4. Move those file to ***location_cert_key***.
5. Edit the ***https_server.conf*** with respective certificate and key path.
6. Link the ***/etc/nginx/sites-available/https_server.conf*** to ***/etc/nginx/sites-enabled/https_server.conf***
7. Add the post script to restart the nginx(***/opt/elasticbeanstalk/hooks/appdeploy/post/99_restart_nginx.sh***).

# Note and FAQs:
Why restart the nginx in post script rather in the Ebextension?

As ebextenstion will execute at the start of the deployment itself when edit the nginx and try to restart the application
initially at that time docker(your application) will not be up and running so I have added the nginx restart as separate script in post deployment.



