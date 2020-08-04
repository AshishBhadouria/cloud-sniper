
<div style="text-align:center"><img src="./images/dashboard.png" alt="Cloud Sniper" width=800px/></div>


## *Cloud Security Operations*

### *What is Cloud Sniper?*

***Cloud Sniper*** is a platform designed to manage Cloud Security Operations, intended to respond to security incidents by accurately analyzing and correlating cloud artifacts. It is meant to be used as a *Cloud Security Operations* platform to detect and remediate security incidents by showing a complete visibility of the company's cloud security posture.

We are presenting a centralized Incident and Response platform, which executes automatic actions, by learning from the analysts' expert knowledge. To do it, only native cloud artifacts and open source technologies are implemented. In this way, the community can extend the project with different security use cases.

***Cloud Sniper*** receives and processes security feeds, providing an automatic response mechanism to protect the cloud infrastructure. To detect attackers' advanced *TTPs*, ***Cloud Sniper Analytics*** module correlates IOCs providing enhanced security findings to the security analyst.

With this platform, you get a complete and comprehensive management system of the security incidents. At the same time, an advanced security analyst can integrate Cloud Sniper with external forensic or incident-and-response tools to ingest new security feeds. The platform automatically deploys and provides cloud-based integration with all native resources, in a fully modularized manner, making it very easy to extend for the community.

Is currently available for *AWS*, but it is to be extended to others cloud platforms.

### Some cool features (terraform | python | docker | Kibana)

1. Security automation (multi-account | multi-region)
   1. Incident and Response automation
   2. IAM activity
2. Cloud Sniper Analytics - Enhanced lambda for C2 detection
3. ELK integration
   1. Docker files
   2. Incident and Response dashboard templates
4. Messaging|Alerts
   1. Slack
   2. Email


### AWS deployment

<div style="text-align:center"><img src="./images/deployment.png" alt="Cloud Sniper" width=800px/></div>

Cloud Sniper uses [terraform](https://www.terraform.io/) to automatically deploy the entire infrastructure. The core is programmed in python, so it can be extended accordingly to any environment.

The requirements include:

1. AWS cli
2. A programmatic_access_key|role for AWS
3. An AWS local profile configured
4. terraform client

To deploy Cloud Sniper you should run:

1. ~$ git clone https://github.com/cloud-sniper/cloud-sniper.git
2. ~$ cd cloud-sniper
3. Set the environment variables corresponding to the account in the variables.tf file
4. Create main.tf file

```
   provider "aws" {
    region                    = "region"
    shared_credentials_file   = "/your-home/.aws/credentials"
    profile                   = "your-profile"
   }
```
5. ~/cloud-sniper$ terraform init
6. ~/cloud-sniper$ terraform plan
7. ~/cloud-sniper$ terraform apply [yes]


### Dashboard  - ELK stack

The dashboard presented above is an example of the Cloud Sniper UI.

We add a basic opendistro ELK terraform deploy to provide visibility of the findings generated by Cloud Sniper. If you already have your own SIEM, your existing pipeline may be used. Import our dashboard to get fast insights. 

To deploy the Cloud Sniper Dashboard, you should run:

1.  ~$ git clone https://github.com/cloud-sniper/cloud-sniper.git
2.  ~$ cd cloud-sniper/dashboard
3.  Set the environment variables corresponding to the account in the variables.tf file
4.  Create main.tf
5.  ~/cloud-sniper/dashboard$ terraform init
6.  ~/cloud-sniper/dashboard$ terraform plan
7.  set your aws ssh-key for get access to the instance and your VPC-ID. (the EC2 access is restricted to the current public IP) 
8.  ~/cloud-sniper/dashboard$ terraform apply [yes]
9.  when the EC2 instance is initialized, you have to manually copy the logstash/logstash.conf file inside '/etc/logstash/conf.d/logstash.conf'. *Remember put your s3 folder name and setup with your user/password*. 

### RELEASES

####  EKOLABS - EKOPARTY Security Conference 2019 (terraform | python | docker)
Authors:  
[Nicolás Rivero Corvalán - Security Automation](https://www.linkedin.com/in/riveronicolas/)  
[Matías Marenchino - Security Analytics](https://www.linkedin.com/in/mlmarenchino/)

####  ARSENAL - BLACK HAT USA 2020 (terraform | python | docker | ELK)
Authors:  
[Nicolás Rivero Corvalán - Security Automation](https://www.linkedin.com/in/riveronicolas/)  
[Matías Marenchino - Security Analytics](https://www.linkedin.com/in/mlmarenchino/)  
[Santiago Friquet - Security Automation](https://www.linkedin.com/in/santiago-friquet/)

### Contact us: <cloudsniper.cba@gmail.com>

### LEGAL
This project is licensed under the terms of the MIT license.

