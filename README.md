

<a href="https://hauke.cloud" target="_blank"><img src="https://img.shields.io/badge/home-hauke.cloud-brightgreen" alt="hauke.cloud" style="display: block;" /></a>
<a href="https://github.com/hauke-cloud" target="_blank"><img src="https://img.shields.io/badge/github-hauke.cloud-blue" alt="hauke.cloud Github Organisation" style="display: block;" /></a>


# Terraform Hop Hop Cluster


<img src="https://raw.githubusercontent.com/hauke-cloud/.github/main/resources/img/organisation-logo-small.png" alt="hauke.cloud logo" width="109" height="123" align="right">


Terraform module to create a Kubernetes cluster with hop-hop-cluster on Hetzner




## 🚀 Getting started
To get started, you need to clone the repository. Follow the steps below:

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



## :wrench: Configuration
This project is configured using the following files:

- `variables.tf`: Defines all the input variables required by the project.
- `terraform.tfvars`: Contains values for the variables defined in `variables.tf`.
- `secrets.enc.yaml`: Encrypted secrets file managed by SOPS, containing sensitive data.

### Configuration Steps

1. **Update `terraform.tfvars`**:
   - Populate the `terraform.tfvars` file with values corresponding to the variables in `variables.tf`.

   Example:
   ```hcl
   variable_name = "your_value"
   ```

  :bangbang: **IMPORTANT**: For a full list of variables, descriptions and default values, please check [this](resources/generated/terraform_settings.md) document.
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
To run this terraform project simply follow the steps below:

### 1. Initialize the projects

The `init`` command prepares your working directory for OpenTofu (or Terraform):

***OpenTofu***
```bash
opentofu init
```

***Terraform (if using terraform)***
```bash
terraform init
```

### 2. Plan the changes

Use the `plan` command to see what changes will be made to your infrastructure:

***OpenTofu***
```bash
openfotu plan
```

***Terraform (if using terraform)***
```bash
terraform apply
```

### 3. Apply the changes

The `apply` command will apply the changes to your infrastructure:

***OpenTofu***
```bash
opentofu apply
```

***Terraform (if using terraform)***
```bash
terraform apply
```

### (Optional) 4. Destroy the resources

If you want to destroy the resources created by OpenTofu or Terraform, you can use the following command:

***OpenTofu***
```bash
openfotu destroy
```

***Terraform (if using terraform)***
```bash
terraform destroy
```



## 📄 License

This Project is licensed under the GNU General Public License v3.0

- see the [LICENSE](LICENSE) file for details.


## :coffee: Contributing

To become a contributor, please check out the [CONTRIBUTING](CONTRIBUTING.md) file.


## :email: Contact

For any inquiries or support requests, please open an issue in this
repository or contact us at [contact@hauke.cloud](mailto:contact@hauke.cloud).

