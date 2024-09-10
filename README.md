# ansible-aws-vpc-ec2
A simple ansible playbook for deploying an ec2 instance into a custom aws vpc

## How to use this playbook?
1. Configure you aws CLI credentials by following [AWS CLI setup](https://docs.aws.amazon.com/cli/v1/userguide/cli-chap-welcome.html)
2. Create an aws profile called "sv-aws-ansible" or whatever you want. You must ensure the profile exists in ~/.aws/{config,credentials} path and match the values for region and profile defined in group_vars/all/aws-default.yml. See [AWS Credentials](https://docs.aws.amazon.com/cli/v1/userguide/cli-configure-files.html)
3. Provision VPC infrastructure. `ansible-playbook aws_playbook.yml -t "vpc"`

<p align="center">
  <img src="https://github.com/user-attachments/assets/0547e1c1-e732-4919-863b-9d47f552b5cb">
  <br>
  <em>Figure 1. Role aws-vpc play output</em>
</p>

<br/>

<p align="center">
  <img src="https://github.com/user-attachments/assets/0b9c2f2f-47ee-4700-ab5c-0b0773621085">
  <br>
  <em>Figure 2. VPC resource in aws</em>
</p>

4. Provision ec2 instances. `ansible-playbook aws_playbook.yml -t "ec2"`

<br/>

<p align="center">
  <img src="https://github.com/user-attachments/assets/49d61c66-abd4-4a86-856b-058d9c906f46">
  <br>
  <em>Figure 3. Role aws-ec2 play output</em>
</p>

<br/>

<p align="center">
  <img src="https://github.com/user-attachments/assets/a52079e2-c5d3-4547-8ec3-57fd1755e8e6">
  <br>
  <em>Figure 4. EC2 resource in aws</em>
</p>

5. Check inventory file `ansible-inventory --graph`

<br/>

<p align="center">
  <img src="https://github.com/user-attachments/assets/6acc91ea-27cb-473c-816a-be7ed22d920f">
  <br>
  <em>Figure 4. Resource inventory </em>
</p>

6. Destroy resources `ansible-playbook aws_playbook.yml -t "destroy"` Note the task *TASK [aws-destroy : Remove all non-main route tables]* is skipped because the vpc did not have any non-main route table

<br/>

<p align="center">
  <img src="https://github.com/user-attachments/assets/03f33447-a426-4d34-a96c-fae9fc383644">
  <br>
  <em>Figure 5. Role aws-destroy play output </em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/61fdc8a6-a9c1-4ed0-9a4d-483f2e6af5f1">
  <br>
  <em>Figure 6. Resource inventory </em>
</p>
