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

