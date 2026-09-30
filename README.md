<!-- llm-readme-management spec=1 commit=b5b313160e3b7d57f2083c8e530186e1220ef0e8 template=terraform model=qwen3.8-27b-q4 digest=f68682b55584 generated=2026-09-30T16:35:48Z -->
<a href="https://hauke.cloud" target="_blank"><img src="https://img.shields.io/badge/home-hauke.cloud-brightgreen" alt="hauke.cloud" style="display: block;" /></a>
<a href="https://github.com/hauke-cloud" target="_blank"><img src="https://img.shields.io/badge/github-hauke.cloud-blue" alt="hauke.cloud Github Organisation" style="display: block;" /></a>
<a href="https://github.com/hauke-cloud/llm-readme-management" target="_blank"><img src="https://img.shields.io/badge/template-terraform-orange" alt="Repository type - terraform" style="display: block;" /></a>


# Template Repository


<img src="https://raw.githubusercontent.com/hauke-cloud/.github/main/resources/img/organisation-logo-small.png" alt="hauke.cloud logo" width="109" height="123" align="right">


<llm header hint="Say whether this is a reusable module or a root module that owns real state.">

This OpenTofu root module is intended to provision a hop-hop-cluster Kubernetes cluster on Hetzner. It is a hauke.cloud template repository: version pins, pre-commit hooks, and CI scaffolding are in place, but no Terraform code exists yet. It targets operators deploying cloud infrastructure under the hauke.cloud house conventions.

</llm>


## :book: Description

<llm description>

This repository is a Terraform module skeleton for deploying a hop-hop-cluster Kubernetes cluster on Hetzner. It follows the hauke-cloud house template and provides the repository structure, tooling pins, and CI scaffolding from which the actual module is built. No Terraform source code is present yet; the repository is a starting point for operators who need to implement the cluster definition.

The skeleton ships with the standard hauke-cloud repository hygiene:

- Pre-commit hooks covering whitespace, secret detection (gitleaks), and VCS hygiene
- Version pins for OpenTofu 1.8.0 (preferred) and Terraform 1.9, honoured via tofuenv or tfenv
- Active GitHub Actions workflows for conventional PR-title validation, stale-issue closing, and thread locking
- A template OpenTofu CI pipeline (`tofu fmt`, `tofu validate`, `tofu plan`, `tflint`, `tofu apply`) that is not yet activated

The repository is part of the `hauke-cloud` organisation and uses the shared `.repository` metadata file consumed by hauke.cloud tooling.

</llm>


## :clipboard: Requirements

<llm requirements hint="Give the Terraform version from .terraform-version and the provider constraints from versions.tf, plus the credentials the providers need.">

- **OpenTofu 1.8.0** (pinned in `.opentofu-version`) or **Terraform 1.9** (pinned in `.terraform-version`), selected via `tofuenv` or `tfenv` respectively.
- **AWS CLI**, configured with `aws configure`. The (template) deploy workflow expects `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` as GitHub secrets and targets the `eu-central-1` region.
- **SOPS**, to decrypt `secrets.enc.yaml` before running any OpenTofu command (`sops -d secrets.enc.yaml > secrets.yaml`).
- **pre-commit**, installed with `pre-commit install` (marked mandatory in `CONTRIBUTING.md`).

No Terraform provider constraints are declared in the repository; no `versions.tf` or provider block exists. No Hetzner credentials or API tokens are referenced anywhere in the tree.

</llm>


## 🚀 Getting started

<llm getting_started hint="terraform init, plan and apply, with the backend configuration the repository actually uses. Say plainly if apply touches real infrastructure.">

1. Clone the repository and enter it.

```bash
git clone https://github.com/hauke-cloud/terraform-hop-hop-cluster.git
cd terraform-hop-hop-cluster
```

2. Install the pre-commit hooks that the repository ships.

```bash
pre-commit install
```

3. Run every hook across the tree to confirm the skeleton is clean.

```bash
pre-commit run --all-files
```

4. Install and select the OpenTofu version pinned in `.opentofu-version` (1.8.0) via tofuenv, or the Terraform version in `.terraform-version` (1.9) via tfenv.

```bash
tfenv install
tfenv use
```

5. At this point the repository is a template skeleton: it contains no `*.tf` files, no `variables.tf`, and no provider configuration, so `tofu init`, `tofu plan`, and `tofu apply` have nothing to operate on. The stated purpose (a Hetzner Kubernetes cluster via hop-hop-cluster) is not yet implemented. The active GitHub workflows enforce PR-title conventions, close stale issues, and lock resolved threads; the OpenTofu deploy pipeline exists only as an inactive `.template` file. Until Terraform code is added, the working result of this setup is a linted, hook-protected skeleton ready for you to author modules.

</llm>


## :airplane: Usage

<llm usage hint="For a reusable module, the central example is a module block with source, version and the required variables filled in from variables.tf. For a root module, show the workflow instead.">

This repository is a template skeleton for hauke.cloud Terraform projects. It ships with pre-commit hooks, tool version pins, and GitHub housekeeping workflows, but contains no Terraform configuration yet. Once you add your `.tf` files, the day-to-day workflow is as follows.

**Install pre-commit hooks**

Run this once after cloning so that hooks fire on every commit:

```bash
pre-commit install
```

Run all hooks across the entire tree before pushing:

```bash
pre-commit run --all-files
```

**Decrypt secrets**

Before any OpenTofu command, decrypt the SOPS-encrypted secrets file:

```bash
sops -d secrets.enc.yaml > secrets.yaml
```

**Plan and apply**

The repository pins OpenTofu 1.8.0 (`.opentofu-version`) and Terraform 1.9 (`.terraform-version`). Use whichever you prefer:

```bash
opentofu init
opentofu plan
opentofu apply
```

To tear down all managed infrastructure:

```bash
opentofu destroy
```

</llm>


## :wrench: Configuration

<llm configuration hint="A table of the variables in variables.tf: name, type, default, required. Point at variables.tf for the full set and mention outputs.tf if it exists.">

This repository is a template skeleton and contains no Terraform code. There is no `variables.tf`, no `outputs.tf`, no `terraform.tfvars`, and no provider configuration anywhere in the tree. The README references `variables.tf` and `terraform.tfvars`, but neither file exists, so there are no Terraform variables to document.

The only configuration file present is `.repository`, which carries machine-readable metadata consumed by hauke.cloud tooling. All values are still template placeholders:

| Name | Value |
|------|-------|
| `title` | `Template Repository` |
| `docker_image_registry` | `ghrc.io` |
| `docker_image_namespace` | `hauke-cloud/example` |
| `docker_image_version` | `latest` |
| `helm_repository` | `https://hauke-cloud.github.io/helm-charts` |
| `helm_chart` | `example` |

The inactive CI workflow template (`.github/workflows/terraform-deploy.yml.template`) expects the following GitHub Actions secrets: `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, and `GITHUB_TOKEN`. The AWS region is hardcoded to `eu-central-1`.

Several files referenced by the README or the workflow template do not exist in the repository: `.tflint.hcl`, `secrets.enc.yaml`, and `resources/generated/terraform_settings.md`. Until Terraform source files are added, no `tofu init` or `tofu validate` can succeed.

</llm>


## :hammer: Development

<llm development hint="Cover terraform fmt, validate, tflint and terraform-docs where the repository configures them.">

There are no tests in this repository. No test framework, test files, or test commands exist.

The only linting and formatting tool that is configured and runnable is pre-commit. Install the hooks once after cloning, then run them before committing:

```bash
pre-commit install
pre-commit run --all-files
```

The hooks check for trailing whitespace, large files, merge-conflict markers, VCS permalinks, private keys, AWS credentials, end-of-file newlines, and secret leaks (via gitleaks).

**CI enforcement.** The active workflow `pr-title.yml` validates every pull-request title against a conventional-commit scheme. Allowed types are `fix`, `feat`, `docs`, `ci`, and `chore`; the subject must begin with an uppercase letter. A `[WIP]` prefix is permitted. A non-conforming title fails the check and blocks the PR.

The OpenTofu pipeline (`tofu fmt -check -diff`, `tofu validate`, `tflint --config .tflint.hcl`) is defined in `.github/workflows/terraform-deploy.yml.template`, which is **not** an active workflow. No `.tf` files or `.tflint.hcl` exist yet, so those commands cannot run. Once Terraform code is added and the template is renamed to `terraform-deploy.yml`, the pipeline will enforce formatting, validation, and tflint on every PR.

No generated files (for example, terraform-docs output) are produced or checked in this repository.

</llm>


## 📄 License

This Project is licensed under the GNU General Public License v3.0

- see the [LICENSE](LICENSE) file for details.


## :coffee: Contributing

To become a contributor, please check out the [CONTRIBUTING](CONTRIBUTING.md) file.


## :email: Contact

For any inquiries or support requests, please open an issue in this
repository or contact us at [contact@hauke.cloud](mailto:contact@hauke.cloud).
