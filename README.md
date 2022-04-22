
# Deploying a High Availability WebApp on AWS

In this project, I deployed web servers for a highly available web app using CloudFormation.

I wrote the script that creates and deploys the network infrastructure and servers from the ground up.

The project consists of two main stacks, one for deploying the networking components, and the other for deploying the servers, security roles, and software.

## Architecture Diagram

![App Screenshot](https://i.imgur.com/kBzLNoa.png)


## Infrastructure Deployment

This project is deployed in two steps the first one is to deploy the Network Infrastructure,
The second is to deploy the servers 

1- to deploy the Network infrastructure run

```bash
./create.sh Network-stack network-infra.yml network-parameters.json
```

2- to deploy the Servers infrastructure, run

```bash
./create.sh Servers-stack servers-infra.yml servers-parameters.json
```

### Verify deployment

To check whether the web application is running,
follow the web application public URL, which could be found in the output tab in the CloudFormation stack.


### Delete Infrastructure

To delete the infrastructure after verifying that it works, run the following command.

1- For the Network infrastructure

```bash
./delete.sh Network-stack
```

2- For the Servers infrastructure

```bash
./delete.sh Servers-stack
```


## Appendix

While Creating the Servers Infrastructure, pay attention to your AWS EC2 vCPUs Limits, 
each account has a default soft limit of 8 vCPUs, and you have to contact AWS Support to extend that limit to meet your needs.

For more information please visit the [EC2 Management Documentation](https://us-west-2.console.aws.amazon.com/ec2/v2/home?region=us-west-2#Limits:) <br/>
And the [EC2 vCPU Calculator](https://us-west-2.console.aws.amazon.com/ec2/v2/home?region=us-west-2#LimitsCalculator:)

