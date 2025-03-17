For creating AKS using terraform have used the Offical documentation of Microsoft :- https://learn.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-terraform?pivots=development-environment-azure-cli

Prerequiste (Use this link for installing all the prerequistes :- https://learn.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-terraform?pivots=development-environment-azure-cli)

Install and configure Terraform.
Download kubectl.
Create a random value for the Azure resource group name using random_pet.
Create an Azure resource group using azurerm_resource_group.
Access the configuration of the AzureRM provider to get the Azure Object ID using azurerm_client_config.
Create a Kubernetes cluster using azurerm_kubernetes_cluster.
Create an AzAPI resource azapi_resource.
Create an AzAPI resource to generate an SSH key pair using azapi_resource_action.


Initialize Terraform

Run terraform init to initialize the Terraform deployment. This command downloads the Azure provider required to manage your Azure resources.
terraform init -upgrade

The -upgrade parameter upgrades the necessary provider plugins to the newest version that complies with the configuration's version constraints.

Run terraform plan Command
terraform plan

The terraform plan command creates an execution plan, but doesn't execute it. Instead, it determines what actions are necessary to create the configuration specified in your configuration files

Run terraform apply to apply the execution plan to your cloud infrastructure.

terraform apply main.tf


