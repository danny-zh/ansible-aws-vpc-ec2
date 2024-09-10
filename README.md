# ansible-aws-vpc-ec2
A simple ansible playbook for deploying an ec2 instance into a custom aws vpc

## How to use this playbook?
1. Configure you aws CLI credentials by following [AWS CLI setup](https://docs.aws.amazon.com/cli/v1/userguide/cli-chap-welcome.html)
2. Create an aws profile called "sv-aws-ansible" or whatever you want. You must ensure the profile exists in ~/.aws/{config,credentials} path and match the values for region and profile defined in group_vars/all/aws-default.yml. See [AWS Credentials](https://docs.aws.amazon.com/cli/v1/userguide/cli-configure-files.html)
3. Provision VPC infrastructure. `ansible-playbook aws_playbook.yml -t "vpc"`

<p align="center">
  <img src="image.png">
  <br>
  <em>Figure 1. Role aws-vpc play output</em>
</p>

<br/>

<p align="center">
  <img src="image-1.png">
  <br>
  <em>Figure 2. VPC resource in aws</em>
</p>

4. Provision ec2 instances. `ansible-playbook aws_playbook.yml -t "ec2"`

<br/>

<p align="center">
  <img src="image-2.png">
  <br>
  <em>Figure 3. Role aws-ec2 play output</em>
</p>

<br/>

<p align="center">
  <img src="image-3.png">
  <br>
  <em>Figure 4. EC2 resource in aws</em>
</p>

5. Check inventory file `ansible-inventory --graph`

<br/>

<p align="center">
  <img src="image-4.png">
  <br>
  <em>Figure 4. Resource inventory </em>
</p>

6. Destroy resources `ansible-playbook aws_playbook.yml -t "destroy"` Note the task *TASK [aws-destroy : Remove all non-main route tables]* is skipped because the vpc did not have any non-main route table

<br/>

<p align="center">
  <img src="image-5.png">
  <br>
  <em>Figure 5. Role aws-destroy play output </em>
</p>

<p align="center">
  <img src="image-6.png">
  <br>
  <em>Figure 6. Resource inventory </em>
</p>
