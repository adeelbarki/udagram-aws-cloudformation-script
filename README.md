# Project: Udagram - A high availability Web App using AWS cloudformation

## Description

In this project a high availability web application is deployed using cloudformation. Code is loaded to S3 storage and then deployed to a web server.

The project is divided in two main parts:

* High Availability(HA) Diagram in order to understand cloudformation script
* Creating a cloudformation script

## Understanding Script 

* Script has different sections that includes Load Balancer, Launch Configuration, AutoScaling, Listener, Security Group, Target Group and Health Check.

* There is an output section where Load Balancer DNS is attached with http in front of it.

* Autoscaling group is assigned a target group 

* Load Balancer has a listener rule associated with same target group

* Port 80 is assigned to security group, health check and listeners that are associated with Load Balancer

* Autoscale instances are assigned a private subnet

* t3.medium is used with 10 GB of disk

* IAM role and instance profile is defined for communication between EC2 and S3 storage.

* NAT Gateway is used between public and private subnets


## Resources 

Project files are provided on github link. Clone the files using below link in terminal.
`$ git clone https://github.com/adeelbarki/udagram-aws-cloudformation-script.git`

Make sure to `$ cd udagram-aws-cloudformation-script` in terminal to access all files. 

## Run the code

### General Command (for Windows / linux users )

Create Stack: 

`aws cloudformation create-stack --stack-name udagramservers --region eu-central-1 --template-body file://udagram-network-server-combined.yml --parameters file://network-parameters.json --capabilities CAPABILITY_IAM`

_Note:_ 
* Region can be selected according to your location. In this case `eu-central-1` is selected.
*  AWS has limited instances in each region. In order to check your limit in specific region, goto EC2 > Limits in AWS console. This script is scaled to 4 instances and may not run if your EC2 limit is less than 4. In case of lower limit ask AWS help team to increase the limit. 
*  If you are linux or mac user you can also use simple script file to create stack using create.sh file. File is provided in this folder.

Update Stack:

`aws cloudformation create-stack --stack-name udagramservers --region eu-central-1 --template-body file://udagram-network-server-combined.yml --parameters file://network-parameters.json --capabilities CAPABILITY_IAM`

In case if you want to update a stack just replace `create` with `update` in command line.


## Testing

Results of the scripts can be seen in aws cloudformation console. In EC2, just goto Load balancer and select specific load balancer. Copy provided DNS and open it in chrome. 

Another way to look at the web page is by going into cloudformation output tab. Click the link with http and results can be seen in the browser. 
Result: `Hello Udacity it works!!`

## License

Project udagram is a part of Udacity DevOps Engineer Nano Degree Program.   

## Author

* Adeel Ahmed Khan (Adeel Barki) <br />
  __ _Full Stack Web Developer_ <br />
  _Front End Web Developer_ <br />
  _React Web Developer_ __ <br />
