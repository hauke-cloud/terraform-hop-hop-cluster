<!-- llm-readme-management spec=1 commit=b5b313160e3b7d57f2083c8e530186e1220ef0e8 template=terraform model=qwen3.6-35b-a3b digest=f68682b55584 generated=2026-09-08T23:57:41Z -->
<a href="https://hauke.cloud" target="_blank"><img src="https://img.shields.io/badge/home-hauke.cloud-brightgreen" alt="hauke.cloud" style="display: block;" /></a>
<a href="https://github.com/hauke-cloud" target="_blank"><img src="https://img.shields.io/badge/github-hauke.cloud-blue" alt="hauke.cloud Github Organisation" style="display: block;" /></a>
<a href="https://github.com/hauke-cloud/llm-readme-management" target="_blank"><img src="https://img.shields.io/badge/template-terraform-orange" alt="Repository type - terraform" style="display: block;" /></a>


# Template Repository


<img src="https://raw.githubusercontent.com/hauke-cloud/.github/main/resources/img/organisation-logo-small.png" alt="hauke.cloud logo" width="109" height="123" align="right">


<llm header hint="Say whether this is a reusable module or a root module that owns real state.">

This OpenTofu module template serves as a scaffold rather than a functional deployment tool. It bundles CI workflows, pre-commit hooks, and version pinning to help infrastructure operators standardize their cluster provisioning pipelines. You can use it as a starting point for your own Terraform or OpenTofu projects.

</llm>


## :book: Description

<llm description>

You need a standardized starting point for deploying Kubernetes clusters on Hetzner Cloud using the hop-hop-cluster module, along with consistent CI/CD and repository hygiene practices. This repository provides that foundation as an OpenTofu and Terraform scaffold, supplying version pinning, pre-commit hooks, and GitHub Actions templates to automate linting, planning, and applying infrastructure changes.

- Scaffolds a Terraform/OpenTofu project for Hetzner Kubernetes deployments via hop-hop-cluster
- Provides CI workflow templates for OpenTofu formatting, validation, planning, and conditional applies
- Configures pre-commit hooks for repository hygiene and security scanning
- Contains GitHub automation workflows for stale issue marking and conventional commit enforcement

It functions as an internal template within the `hauke-cloud` organization, establishing baseline configurations and automation patterns for shared infrastructure modules.

</llm>


## :clipboard: Requirements

<llm requirements hint="Give the Terraform version from .terraform-version and the provider constraints from versions.tf, plus the credentials the providers need.">

- OpenTofu 1.8.0 (preferred) or Terraform 1.9+
- `tofuenv` or `tfenv` for version management
- AWS CLI installed and configured with `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` credentials
- SOPS, to decrypt encrypted secrets
- tflint, for linting configuration files
- pre-commit framework, for repository hygiene hooks

</llm>


## 🚀 Getting started

<llm getting_started hint="terraform init, plan and apply, with the backend configuration the repository actually uses. Say plainly if apply touches real infrastructure.">

1. Clone the repository and enter its directory.
```bash
git clone https://github.com/hauke-cloud/terraform-hop-hop-cluster.git
cd terraform-hop-hop-cluster
```

2. Initialize the module using OpenTofu or Terraform.
```bash
opentofu init
```

3. Preview the infrastructure changes before applying them.
```bash
opentofu plan
```

4. Apply the configuration to provision your cluster.
```bash
opentofu apply
```

</llm>


## :airplane: Usage

<llm usage hint="For a reusable module, the central example is a module block with source, version and the required variables filled in from variables.tf. For a root module, show the workflow instead.">

You work with this repository by configuring local development tools, initializing your infrastructure state, and validating code quality before deployment. The project provides version pinning files and a pre-commit configuration to standardize your environment.

Install the local hooks defined in `.pre-commit-config.yaml` to enforce formatting, detect secrets, and check for merge conflicts before each commit:
```bash
pre-commit install
```

Once you add your source files, initialize the working directory using your preferred CLI. The repository pins OpenTofu 1.8.0 in `.opentofu-version` and Terraform 1.9 in `.terraform-version`. Run initialization to download providers:
```bash
opentofu init
```

Preview and apply changes through the standard lifecycle commands, while running the CI validation steps locally to catch issues early. The repository documentation references `opentofu plan`, `opentofu apply`, and `opentofu destroy` for managing state, alongside `tofu fmt -check -diff`, `tofu validate`, and `tflint --config .tflint.hcl` for quality checks:
```bash
opentofu plan
tofu fmt -check -diff
tofu validate
tflint --config .tflint.hcl
```

</llm>


## :wrench: Configuration

<llm configuration hint="A table of the variables in variables.tf: name, type, default, required. Point at variables.tf for the full set and mention outputs.tf if it exists.">

This repository is a scaffold template and currently contains zero Terraform source files. Consequently, it exposes no input variables, outputs, or resource configurations. The intended configuration surface would reside in `variables.tf` for module inputs and `outputs.tf` for exported values, but neither file exists in the current filesystem state.

The documentation references placeholder files that define where configuration should live once the module is populated:
- `variables.tf`: Would hold all input variables (name, type, default, required). Point to this file for the full variable set when available.
- `terraform.tfvars`: Intended for overriding variable defaults.
- `secrets.enc.yaml`: Referenced for SOPS-managed encrypted secrets.

The CI workflow template expects you to configure two environment variables in GitHub Secrets: `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`. Note that while the project description targets Hetzner Cloud, the CI template hardcodes AWS credentials and region `eu-central-1`. All referenced Terraform configuration files are currently missing from the repository. Once populated, point to `variables.tf` for the full variable set and check `outputs.tf` for exported values.

</llm>


## :hammer: Development

<llm development hint="Cover terraform fmt, validate, tflint and terraform-docs where the repository configures them.">

To contribute changes, ensure your environment matches the pinned versions in `.terraform-version` and `.opentofu-version`. Install local pre-commit hooks to enforce repository hygiene before each commit:
```bash
pre-commit install
```
You can manually trigger all checks against every file with:
```bash
pre-commit run --all-files
```
The CI pipeline enforces formatting, validation, and linting on pull requests. Run these commands locally to avoid failures:
```bash
tofu fmt -check -diff
tofu validate
tflint --config .tflint.hcl
```
If you use Terraform instead of OpenTofu, substitute `tofu` with `terraform`. The repository also requires conventional commit messages for pull request titles. A GitHub Actions workflow validates this automatically; you may prefix draft or work-in-progress titles with `[WIP]`. Any generated documentation files must be regenerated and committed alongside your changes before opening a pull request. Update hook revisions periodically using:
```bash
pre-commit autoupdate
```

</llm>


## 📄 License

This Project is licensed under the GNU General Public License v3.0

- see the [LICENSE](LICENSE) file for details.


## :coffee: Contributing

To become a contributor, please check out the [CONTRIBUTING](CONTRIBUTING.md) file.


## :email: Contact

For any inquiries or support requests, please open an issue in this
repository or contact us at [contact@hauke.cloud](mailto:contact@hauke.cloud).
