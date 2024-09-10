

<a href="https://hauke.cloud" target="_blank"><img src="https://img.shields.io/badge/home-hauke.cloud-brightgreen" alt="hauke.cloud" style="display: block;" /></a>
<a href="https://github.com/hauke-cloud" target="_blank"><img src="https://img.shields.io/badge/github-hauke.cloud-blue" alt="hauke.cloud Github Organisation" style="display: block;" /></a>


# Terraform Hop Hop Cluster


<img src="https://raw.githubusercontent.com/hauke-cloud/.github/main/resources/img/organisation-logo-small.png" alt="hauke.cloud logo" width="109" height="123" align="right">


Terraform module to create a Kubernetes cluster with hop-hop-cluster on Hetzner




## 🚀 Getting started
To get started, you need to clone the repository containing this `README.md` file. Follow the steps below:

### 1. Clone the repository

Use the following command to clone the repository:

```bash
git clone https://github.com/hauke-cloud/terraform-hop-hop-cluster.git
```

### 2. Navigate to the repository directory

Once the repository is cloned, navigate to the directory:

```bash
cd terraform-hop-hop-cluster
```

### 3. Check the content

```bash
ls -la
```

This will display all the files and directories in the cloned repository.

## Prerequisites

Before using this project, make sure you have the following prerequisites:

### 1. OpenTofu (Recommended) or Terraform with Version Management

#### OpenTofu
We recommend using [OpenTofu](https://opentofu.org) for infrastructure management.

- **Version**: The required version is specified in the `.opentofu-version` file. OpenTofu automatically reads this file to ensure the correct version is used.
- **Installation Guide**: Follow the [OpenTofu installation instructions](https://opentofu.org/docs/getting-started/install.html).

#### Terraform (Optional)
Alternatively, you can use [Terraform](https://www.terraform.io/), though OpenTofu is preferred. If you choose to use Terraform, ensure you have [tfenv](https://github.com/tfutils/tfenv) installed to manage the correct version based on the `.terraform-version` file.

- **Version**: The required version is specified in the `.terraform-version` file. Use `tfenv` to install the version specified:
    ```bash
    tfenv install
    tfenv use
    ```
- **Installation Guide**: Follow the [Terraform installation instructions](https://learn.hashicorp.com/tutorials/terraform/install-cli).

### 2. Cloud Provider CLI Installed (AWS)

For managing AWS infrastructure, ensure that the AWS CLI is installed and configured:

- **Install the AWS CLI**: [AWS CLI Installation Guide](https://aws.amazon.com/cli/)
- **Configure using AWS CLI**: Run `aws configure` if you haven't already.

### 3. Required Environment Variables

Make sure the following environment variables are set up for proper access:

- **AWS_PROFILE**: The AWS profile that allows you to assume the appropriate AWS role and access the OpenTofu/Terraform S3 state bucket. Configure your AWS CLI profiles with the necessary role-assumption details in your `~/.aws/config` file.

    ```bash
    export AWS_PROFILE="your-aws-profile-name"
    ```

- **GITHUB_APP_ID**: The GitHub App ID used for managing the README and other repository settings.

    ```bash
    export GITHUB_APP_ID="your-github-app-id"
    ```

- **GITHUB_APP_INSTALLATION_ID**: The installation ID of the GitHub App for readme-management.

    ```bash
    export GITHUB_APP_INSTALLATION_ID="your-github-app-installation-id"
    ```

- **GITHUB_APP_PEM_FILE**: The private key (PEM) file path associated with your GitHub App.

    ```bash
    export GITHUB_APP_PEM_FILE="/path/to/your/github-app.pem"
    ```



## :wrench: Configuration
This project is configured using the following files:

- `variables.tf`: Defines all the input variables required by the project.
- `terraform.tf`: Contains values for the variables defined in `variables.tf`.
- `secrets.enc.yaml`: Encrypted secrets file managed by SOPS, containing sensitive data.

### Configuration Steps

1. **Update `terraform.tf`**:
   - Populate the `terraform.tf` file with values corresponding to the variables in `variables.tf`.

   Example:
   ```hcl
   variable_name = "your_value"
   ```
2. **Decrypt `secrets.enc.yaml`**:

   - Use SOPS to decrypt the secrets file before running any Terraform commands:

   ```shell
   sops -d secrets.enc.yaml > secrets.yaml
   ```

   **Important**: Do not commit the decrypted `secrets.yaml` file to version control.

3. **Encrypt secrets (if modified):**
   - After modifying the `secrets.yaml` file, re-encrypt it with SOPS:

   ```shell
   sops secrets.yaml > secrets.enc.yaml
   ```

  - Delete the decrypted `secrets.yaml` to keep sensitive data secure.



## :airplane: Usage
Before deploying the Terraform code, you need to set up some environment
variables. These variables are required for authenticating with AWS
and GitHub. Follow the steps below:

### 1. Initialize Terraform

Before applying the Terraform code, initialize the Terraform working directory:

```bash
terraform init
```

### 2. Apply Terraform Configuration

To deploy the infrastructure, use the following command:

```bash
terraform apply
```

This command will read the configuration settings from the `terraform.tfvars`
file and provision the resources in your AWS account.3

### 3. Destroy Terraform Resources (Optional)

If you need to destroy the resources created by Terraform, you can use the following command:

```bash
terraform destroy
```

This will remove all resources defined in the Terraform configuration from your AWS account.



## 📄 License

This Project is licensed under the GNU General Public License v3.0

- see the [LICENSE](LICENSE) file for details.


## :coffee: Contributing

To become a contributor, please check out the [CONTRIBUTING](CONTRIBUTING.md) file.


## :email: Contact

For any inquiries or support requests, please open an issue in this
repository or contact us at [contact@hauke.cloud](mailto:contact@hauke.cloud).

