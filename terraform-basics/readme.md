# Terraform Basics
Terraform is an IaC tool that uses Hashicorp Configuration Language (HCL) to manage and define resources in code.

## Language Context and Syntax 
Two basic language elements:
* **Blocks** - represents and encapsulates configurations. These are keywords provided right before the start of a specific block, e.g., `provider "azurezm" {}`
  * `terraform`- typically in a terraform.tf file, configures aspects of terraform itself. 
  * `provider` - providers are specified which allow terraform to interact with service providers apis. Each provider is responsible for understanding the resources available within its domain
  * `resource` - Represent objects that terraform manages 
  * `variable` - Defines variables used in resource files. Allow you to parameterize your configurations 
  * `module` - Shared Resource(s) configuration that can be shared across projects and environments 
  * `data` - Allows terraform to dynamically gather information about resources and infrastructure 
  * `output` - Used to output information between resources in terraform or output elsewhere as needed
  * `lifecycle` - How terraform manages the lifecycle of a resource - creates, updates and deletes
  * `locals` - A way to assign a name to an expression or value that can be reused throughout your configuration 
  * `provisioner` - are used to run scripts on a local machine or remote resource. Are considered a last resort and should be used sparingly. 
* **Arguments** - key-value pair used in blocks to specify infrastructure 

--- 

## Core Terraform Workflow 
Core Terraform Workflow is the lifecycle of an end user using terraform to manage the state of their infrastructure. 
The lifecycle can be defined as:
* Write/Update - Utilize HCL to write the terraform configuration files 
  * Initialize Working Directory - `terraform init` - download/install required plugins, initialize backend for storing state and downloads and installs modules
* Plan - Create an execution plan, `terraform plan`. This command reads current state and compares it to new state. It makes recommendations and shows the delta of what will happen if we apply the plan
* Apply - Apply the plan, with `terraform apply`. This asks for confirmation, executes proposed actions, updates state file and outputs any values specified in output blocks
* Destroy - `terraform destroy` will destroy all resources in your current state 

Best practices with terraform workflow:
* CI/CD Pipeline - for automated testing and deployment of updated states 
* Version Control - Utilize git or another vcs to manage versions update 
* State Management Backup - Backup with remote backends such as S3 or Terraform cloud
* Workspace Management - Manage multiple environments/workspaces for code reusability. 

--- 

## Terraform State Management 
Terraform state is a critical component of IaC. It enables management and tracking of resources that have been provisioned.
What is Terraform State?
* information about the state of managed resources by terraform
* Maps the defined configs to real-world resources
* Uses the state to determine what actions are required to achieve desired state (old state vs new state)

**Best Practices**:
* Use separate state files for different environments 
* Use Remote State Storage when possible
* State files contain sensitive information - ensure encrypted at rest and in transit and never store them in vcs (git)

**Useful Commands**:
- `terraform state list` - to list current resources terraform is managing
- `terraform state show <resource>` - to show current resource attributes 
- `terraform state rm <resource>` - remove the resource from the terraform state without actually deleting the resource. If you run terraform apply afterward, terraform will try to create it. You will need to import it.
- `terraform import <resource_addr> <resource_id>` - to import an existing resource. 

Utilize Terraform Workspaces to manage multiple states for different environments, in separate state files. Can easily switch between environments. 