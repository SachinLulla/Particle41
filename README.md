"# Particle41-devops-challenge-senior" 
Welcome to the Particle41 DevOps Team Challenge
This challenge is for candidates who want to join the Particle41 DevOps team.

It is designed to assess your level of familiarity with common modern development and operations tools and concepts.

Summary
We aim to hire software engineers who embrace the DevOps mindset, especially taking an infrastructure-as-code approach to software and infrastructure deployment.

This challenge is designed to evaluate your abilities in the following technologies and concepts:

Software development (in general), by creating an extremely minimal web service.
Containers, including creating a container image from scratch and publishing it.
Public Cloud, including Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Computing (GCP)
Container Deployment/Hosting, such as AWS Kubernetes (EKS), AWS ECS, AWS Lambda, or their Azure or GCP counterparts
Terraform, including writing a module and using it to deploy infrastructure.
Documentation, including a short blurb about the purpose/contents of your repo as well as simple deployment instructions.
This assessment consists of two parts, with an extra-credit section at the end. The first part asks you to create a small application and containerize it. The second part asks you to create a terraform module to deploy a VPC, the necessary ECS/EKS/Lambda (or Azure/GCP equivalent) infrastructure required, and deploy the application to it.

When you have finished your challenge and your repository is ready for review, please tell us at careers@particle41.com. Remember to include the URL to your repository.

Documentation is MANDATORY
It is mandatory to include documentation for your repository explaining how to use it.

Imagine that someone with less experience than you will need to clone your repository and deploy your container, or deploy your terraform infrastructure.

With that in mind, you must provide all the instructions they will need to do that successfully. These must include any prerequisites for deployment; mention of needed tools and links to their installation pages; how to configure credentials for the tool of your choice; and what commands to run for deploying your code.

We want to see your ability to properly document and communicate about your work with the team.

Add a README.md to the root directory of your project, with instructions for the team to deploy the projects you created. Include any notes (purpose, etc.) that you might add to the README if this were a real project.
Publish your code to a public Git repository in a platform of your choice (e.g. GitHub, GitLab, Bitbucket, etc.), so that it can be cloned by the team.
A word about generative AI
It is ok to use generative AI to complete this challenge, but we want to be sure that you know what you're doing.

The acceptance criteria for the solution are clearly defined below. Regardless of using generative AI, your solution must pass those acceptance criteria. If it passes, we're ok with it and you'll move on to the next step in the selection process.

So, this is our advice: if you use generative AI, make sure that your solution works as expected, well passes the criteria as explained below, and perhaps addresses some extra credit. Don't waste our time (and yours!) submitting a solution that doesn't work.

Task 1 - Minimalist Application Development / Docker / Kubernetes
Tiny App Development: 'SimpleTimeService'
Create a simple microservice (which we will call "SimpleTimeService") in any programming language of your choice: Go, NodeJS, Python, C#, Ruby, whatever you like.
The application should be a web server that returns a pure JSON response with the following structure, when its / URL path is accessed:
{
  "timestamp": "<current date and time>",
  "ip": "<the IP address of the visitor>"
}
Dockerize SimpleTimeService
Create a Dockerfile for this microservice.
Your application MUST be configured to run as a non-root user in the container.
Build SimpleTimeService image
Publish the image to a public container registry (for example, DockerHub) so we can pull it for testing.
Push your code to a public git repository
Push your code to a public git repository in the platform of your choice (e.g. GitHub, GitLab, Bitbucket, etc.). MAKE SURE YOU DON'T PUSH ANY SECRETS LIKE API KEYS TO A PUBLIC REPO!
We have a recommended repository structure here.
Acceptance Criteria
Your task will be considered successful if a colleague is able to build/run your container, and the application gives the correct response.

docker build must be the only command needed to build your container, and docker run must be the only command needed to run your container. Your container must run and stay running.

Other criteria for evaluation will be:

Documentation: you MUST add a README file with instructions to deploy your application.
Code quality and style: your code must be easy for others to read, and properly documented when relevant.
Container best practices: your container image should be as small as possible, without unnecessary bloat.
Container best practices: your application MUST be running as a non-root user, as specified in the exercise.
Task 2 - Terraform and Cloud: create the infrastructure to host your container.
Using Terraform, create the following infrastructure in AWS (or equivalent):

If server-based:
A VPC with 2 public and 2 private subnets.
An ECS/EKS or equivalent cluster deployed to that VPC.
A ECS/EKS task/service resource to run your container
The tasks and/nodes must be on the private subnets only.
A load balancer deployed in the public subnets to offer the service.
If serverless:
A VPC with 2 public and 2 private subnets.
A Lambda or equivalent function running your container
Appropriate configuration to associate the function with the private subnets.
An API Gateway, CDN, or loadbalancer to trigger your function
If you prefer, you may use popular modules from the Terraform registry (for example the VPC and EKS modules).

Push your code to a public git repository
Push your code to a public git repository in the platform of your choice (e.g. GitHub, GitLab, Bitbucket, etc.). MAKE SURE YOU DON'T PUSH ANY SECRETS LIKE API KEYS TO A PUBLIC REPO!
We have a recommended repository structure here.
Acceptance Criteria
Your task will be considered successful if a colleague is able to deploy the infrastructure to an appropriate cloud account, the correct resources are created, and the web application gives the correct response.

terraform plan
and

terraform apply
must be the only commands needed to create the infrastructure and deploy the container.

You MUST NOT commit any credentials to the git repository. Instead, provide instructions in the README about how to authenticate to AWS to deploy the infrastructure.

Other criteria for evaluation will be:

Code quality and style: your code must be easy for others to read, and properly documented when relevant.
Terraform best practices: Use variables in your infrastructure root module, and provide some good defaults in a terraform.tfvars file.
Notes, Suggestions, and the opportunity to 'show off'!
Suggested Repo Structure
.
├── app <-- app files/directories and Dockerfile go here
└── terraform <-- Terraform files/directories go here (i.e. we will run `terraform plan`/`terraform apply` from here)
Extra Credit!
THIS SECTION IS COMPLETELY OPTIONAL! THERE IS NO PENALTY FOR IGNORING THIS!

Are you an overachiever? Demonstrate your mastery of cloud-native IaC tooling by doing any of these:

Code to initialize and use a remote Terraform backend (S3 and DynamoDB) for state and locking instead of a local .tfstate file.
Create a simple CI/CD pipeline (Github Actions, Bitbucket Pipelines, GitLab CI, etc.) to execute your docker build, publish your container image to the container registry, and apply your terraform.
Anything else that might demonstrate that you know what's up.




Instructions for TASK 1 - Minimalist Application Development / Docker / Kubernetes


Prerequisites
Before you begin, ensure that you have the following tools installed:

1. Docker
Docker is needed to build, run, and manage containers.

Installation Guide: Docker Installation
Verify installation:
docker --version

2. Git
Git is needed to clone the repository to your local machine.

Installation Guide: Git Installation
Verify installation:
git --version



Clone the Repository
To get started, clone the repository to your local machine:

git clone https://github.com/SachinLulla/Particle41-devops-challenge-senior.git
Navigate into the project directory:

cd SimpleTimeService

Build the Docker Image
Once you've cloned the repository, you can build the Docker image using the following command:

docker build -t  simple-time-service .

where -t Task 1 Minimalist Application Development tags the image with the name simple-time-service.
This command may take a few minutes as it pulls the necessary dependencies.


Run the Docker Container

Once the image is built, you can run the Docker container. This will start the application on port 5000.

To run the container in the background:

docker run -d -p 5000:5000 simple-time-service
-d runs the container in detached mode (in the background).
-p 5000:5000 binds port 5000 of the container to port 5000 on your local machine.

Access the Application
After the container is running, you can access the SimpleTimeService by navigating to the following URL in your web browser:

📌 URL: http://localhost:5000


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


