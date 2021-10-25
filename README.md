# Secured-PHP-Website-With-Custom-VPC

## (Deployed on AWS Cloud)
Here is a project of deploying a PHP website with a database. The baseline of the project is that there is a small PHP website and a database server that needs to be configured with high security. To fulfilling these concerns I'have build infrastructure via custom VPC and security groups providing maximum security.

The VPC is configured with 2 public subnets and 1 private subnet. In which the PHP website and the bastion server are deployed in the public subnet whereas the database instance is in the private subnet. Both the public subnet is routed using the route tables to the Internet gateway via Route 53, which makes the site publicly accessible to the outside world. Still, the database instance is in the private subnet, needs to communicate with the internet. For the same, NAT gateway is configured to map private IP address to public address on the way out and vice versa on the way in. So I have configured a private routing using the route table towards the NAT gateway. The NAT gateway configured with the elastic IP will communicate with the IGW towards the outside world through Route 53 and get back the results and rerouted to the database instance.

For establishing maximum security for the instances, implemented with restricted direct access towards to the website instance and the database instance. Here comes the importance of the bastion server, where the bastion server is configured with a security group in which providing the access to admin/creators of the website and DB. From that bastion server, only those authorized users can access both the website instance and the DB instance. In the same manner, the website instance security group is enabled with site-required ports and also the bastion server authorization. The DB instance also enabled the security group with the database requirement ports for the website and the bastion server authorization as the same as the earlier. NACL is also configured with subnet-level protection for the infrastructure.

## Features

- High Security implemented infrastructure.
- Easy configuration to implement.
- Avoids data breaches by implementing an isolated space.

## Used Resources

- VPC
- Route 53
- NAT Gateway
- Route tables
- Elastic IP
- Internet Gateway
- EC2 Instances
- Security groups
- Network Access Control List




## Architecture

![alt text](https://github.com/rony-james/Highly-Secured-PHP-Website-With-Custom-VPC/blob/main/ddr5.jpeg?raw=true)


## Conclusion
Here it was an AWS-based project for a website configured with custom VPC and provided with maximum security.
