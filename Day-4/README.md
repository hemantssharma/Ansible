# GCP VPC and Firewall Rules Ansible Playbook

This Ansible playbook retrieves VPC details and creates firewall rules to allow SSH, HTTP, and HTTPS traffic in a specified Google Cloud Platform (GCP) project.

## Prerequisites

**Ansible installed on your local machine:**
```
sudo apt update
sudo apt install ansible
```
**Install google collection:**
```
ansible-galaxy collection install google.cloud
```
**Install pip and google-auth:**
```
sudo apt install pip
sudo pip install google-auth
```
**GCP service account with the necessary permissions:**
Service account key file in JSON format.

## Playbook Configuration

**Hosts:**
```
localhost
```

Update the following variables in the playbook as needed:

- `project`: Your GCP project ID.
- `service_account_file`: Path to your service account JSON key file.
- `filters`: Filter to specify the VPC name.


## Playbook Details

- **Retrieve VPC Details:**

    The playbook retrieves details of the specified VPC using the `google.cloud.gcp_compute_network_info` module.

- **Create Firewall Rules:**

    The playbook creates firewall rules to allow SSH, HTTP, and HTTPS traffic using the `google.cloud.gcp_compute_firewall` module.


- **Run the playbook using the following command:**
```
ansible-playbook <playbook_name>
```

**Author**
```
Hemant Sharma
```
