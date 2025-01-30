# Ansible

#_Ansible Playbook: Create GCP VPC, Subnets, Firewall Rules, and VM

#_Overview:
This Ansible playbook creates a VPC, subnets, firewall rules, and a VM instance on Google Cloud Platform (GCP). It uses GCP modules to manage the resources.

#_Prerequisites:

#Ansible installed on your local machine:
```
sudo apt update
sudo apt install ansible
```
#Install google collection:
ansible-galaxy collection install google.cloud

#Install pip and google-auth:
sudo apt install pip && sudo pip install google-auth

#GCP service account with the necessary permissions.
#Service account key file in JSON format.

#_Playbook Details:

#Playbook Name:
vpc-subnet-firewall_rule-vm-creation.yml

#_Hosts:
localhost


#_Variables:
project_id: GCP project ID.
region: GCP region.
vpc_name: Name of the VPC.
subnet_1_name: Name of the first subnet.
subnet_2_name: Name of the second subnet.
firewall_rule_internal: Name of the internal traffic firewall rule.
firewall_rule_ssh: Name of the SSH firewall rule.
firewall_rule_http_https: Name of the HTTP/HTTPS firewall rule.
network_self_link: SelfLink of the VPC.
service_account_file: Path to the service account key file.


#_Tasks:


1. Set GOOGLE_APPLICATION_CREDENTIALS Environment Variable

Module: ansible.builtin.set_fact
Description: Sets the environment variable for Google Cloud authentication.
Parameters:
ansible_env: Dictionary containing the environment variable.

2. Create VPC Network

Module: google.cloud.gcp_compute_network
Description: Creates a VPC network.
Parameters:
name: Name of the VPC.
auto_create_subnetworks: Whether to auto-create subnetworks.
project: GCP project ID.
auth_kind: Authentication method.
service_account_file: Path to the service account key file.

3. Create Subnet 1

Module: google.cloud.gcp_compute_subnetwork
Description: Creates the first subnet.
Parameters:
name: Name of the subnet.
region: GCP region.
ip_cidr_range: CIDR range for the subnet.
project: GCP project ID.
network: SelfLink of the VPC.
auth_kind: Authentication method.
service_account_file: Path to the service account key file.

4. Create Subnet 2

Module: google.cloud.gcp_compute_subnetwork
Description: Creates the second subnet.
Parameters:
name: Name of the subnet.
region: GCP region.
ip_cidr_range: CIDR range for the subnet.
project: GCP project ID.
network: SelfLink of the VPC.
auth_kind: Authentication method.
service_account_file: Path to the service account key file.

5. Create Firewall Rule to Allow Internal Traffic

Module: google.cloud.gcp_compute_firewall
Description: Creates a firewall rule to allow internal traffic within the VPC.
Parameters:
name: Name of the firewall rule.
network: SelfLink of the VPC.
project: GCP project ID.
allowed: List of allowed protocols and ports.
source_ranges: Source IP ranges.
direction: Direction of the traffic.
priority: Priority of the rule.
target_tags: Target tags for the rule.
state: Desired state of the firewall rule.
auth_kind: Authentication method.
service_account_file: Path to the service account key file.

6. Create Firewall Rule to Allow SSH

Module: google.cloud.gcp_compute_firewall
Description: Creates a firewall rule to allow SSH traffic.
Parameters:
name: Name of the firewall rule.
network: SelfLink of the VPC.
project: GCP project ID.
allowed: List of allowed protocols and ports.
source_ranges: Source IP ranges.
direction: Direction of the traffic.
priority: Priority of the rule.
target_tags: Target tags for the rule.
state: Desired state of the firewall rule.
auth_kind: Authentication method.
service_account_file: Path to the service account key file.

7. Create Firewall Rule to Allow HTTP and HTTPS

Module: google.cloud.gcp_compute_firewall
Description: Creates a firewall rule to allow HTTP and HTTPS traffic.
Parameters:
name: Name of the firewall rule.
network: SelfLink of the VPC.
project: GCP project ID.
allowed: List of allowed protocols and ports.
source_ranges: Source IP ranges.
direction: Direction of the traffic.
priority: Priority of the rule.
target_tags: Target tags for the rule.
state: Desired state of the firewall rule.
auth_kind: Authentication method.
service_account_file: Path to the service account key file.

8. Create a VM Instance in the VPC and Subnet

Module: google.cloud.gcp_compute_instance
Description: Creates a VM instance in the specified VPC and subnet.
Parameters:
name: Name of the VM instance.
machine_type: Machine type for the VM.
zone: GCP zone.
project: GCP project ID.
auth_kind: Authentication method.
service_account_file: Path to the service account key file.
network_interfaces: Network interfaces for the VM.
disks: Disks to attach to the VM.
metadata: Metadata for the VM.
tags: Tags for the VM.
labels: Labels for the VM.
service_accounts: Service accounts for the VM.


#_Ensure you have the necessary prerequisites installed and configured.
Update the playbook with your specific details (e.g., project ID, region, VPC name, service account file path).


#_Run the playbook using the following command:
ansible-playbook vpc-subnet-firewall_rule-vm-creation.yml


Author
Hemant Sharma
