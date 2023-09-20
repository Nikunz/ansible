# AWS EC2 Instance Launch Using Ansible #

This repository contains Ansible code to launch AWS EC2 instances in the `us-east-1` region. This playbook will create two `t2.micro` instances using the specified Amazon Machine Image (AMI), security group, and VPC subnet. The instances will also be assigned public IP addresses and tagged with the name "ansible.demo".

## Prerequisites

Before running this Ansible playbook, ensure you have the following prerequisites in place:

1. **Ansible**: Make sure Ansible is installed on the system where you intend to run this playbook. You can install Ansible by following the [official documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

2. **AWS Credentials**: Ensure you have AWS credentials set up properly, either using environment variables, AWS CLI configuration, or an IAM role with the necessary permissions.

## Usage

1. Clone this repository to your local machine or download the `main.yml` playbook file.

2. Modify the playbook file (`main.yml`) if needed, specifically the values for `key_name`, `image`, `group`, `vpc_subnet_id`, and any other parameters you wish to customize.

3. Run the Ansible playbook using the following command:

   ```bash
   ansible-playbook main.yml
   ```

   This command will execute the playbook, and Ansible will launch the specified EC2 instances in the `us-east-1` region.

## Playbook Details

Here is a breakdown of the tasks performed by the Ansible playbook:

```yaml
- name: launching AWS instance using Ansible
  ec2:
    key_name: ansible
    region: us-east-1
    instance_type: t2.micro
    image: ami-0f844a9675b22ea32
    group: default
    count: 2
    vpc_subnet_id: subnet-0ecab2c81f1a8aa57
    assign_public_ip: yes
    instance_tags:
      Name: ansible.demo
```

- `key_name`: The name of the SSH key pair to use for accessing the instances. Change this to your preferred key name.

- `region`: The AWS region where the instances will be launched (`us-east-1` in this example).

- `instance_type`: The type of EC2 instance to launch (`t2.micro` in this example).

- `image`: The ID of the Amazon Machine Image (AMI) to use for the instances.

- `group`: The name of the security group to associate with the instances.

- `count`: The number of instances to launch (2 in this example).

- `vpc_subnet_id`: The ID of the VPC subnet where the instances will be placed.

- `assign_public_ip`: Whether to assign a public IP address to the instances (`yes` in this example).

- `instance_tags`: Tags to assign to the instances. In this case, the instances will be tagged with the name "ansible.demo".

