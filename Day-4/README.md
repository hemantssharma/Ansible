# GCP VPC and Firewall Rules Ansible Playbook

This Ansible playbook retrieves VPC details and creates firewall rules to allow SSH, HTTP, and HTTPS traffic in a specified Google Cloud Platform (GCP) project.

## Prerequisites

- Ansible installed on your local machine
- GCP project with necessary permissions
- Service account JSON key file for authentication

## Environment Setup

1. **Install Ansible:**

    ```sh
    sudo apt-get update
    sudo apt-get install ansible
    ```

2. **Install Ansible GCP Collection:**

    ```sh
    ansible-galaxy collection install google.cloud
    ```

3. **Set up GCP Authentication:**

    - Ensure you have a service account JSON key file.
    - Set the `GOOGLE_APPLICATION_CREDENTIALS` environment variable to the path of your JSON key file:

    ```sh
    export GOOGLE_APPLICATION_CREDENTIALS="/path/to/your/service-account-file.json"
    ```

## Playbook Configuration

Update the following variables in the playbook as needed:

- `project`: Your GCP project ID.
- `service_account_file`: Path to your service account JSON key file.
- `filters`: Filter to specify the VPC name.

## Usage

1. **Clone the repository:**

    ```sh
    git clone https://github.com/yourusername/gcp-vpc-firewall-playbook.git
    cd gcp-vpc-firewall-playbook
    ```

2. **Run the playbook:**

    ```sh
    ansible-playbook playbook.yml
    ```

## Playbook Details

- **Retrieve VPC Details:**

    The playbook retrieves details of the specified VPC using the `google.cloud.gcp_compute_network_info` module.

- **Create Firewall Rules:**

    The playbook creates firewall rules to allow SSH, HTTP, and HTTPS traffic using the `google.cloud.gcp_compute_firewall` module.
