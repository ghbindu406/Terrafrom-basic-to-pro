**Must cover topics in terrafrom **
1. Infrastructure as Code and IaC tools
2. What Is Terraform?
3. Terrafrom Architecture
4. Terraform Lifecycle
5. Terraform Core Concepts
6.Terraform Installation
7. Terraform Providers
8. Terraform Configuration Files
9. Getting Started Using Terraform
10.Import Existing Infrastructure

        3. Terrafrom architecture
            Mainly consist of 2 types
              1. Terrafrom core : Terraform core is responsible for reading configurations and building the dependency Th The 
                  graph.
              2. Terrafrom providers: A provider in Terraform is a plugin that enables interaction with an API. This includes 
                 Cloud providers and Software-as-a-service providers. The providers are specified in the Terraform 
                 configuration code. They tell Terraform which services it needs to interact with.
   
The entire architecture of Terraform, including the two components; Core and Providers. 
4. Terrafrom Lifecycle: Terraform lifecycle consists of – init, plan, apply, and destroy
 Commands: 
  {4.a. Terrafrom init - command initializes a working directory containing configuration files and installs plugins for 
       required providers This is the first thing we do when we start working with terrafrom 
  4.b. Terrafrom Plan - Dry run -- Which is used to generate an execution plan, showing what changes will be made to the 
       infrastructure without actually applying them. It serves as a dry run to visualize the impact of your Terraform 
       configurations.
         Terrafrom plan -out {The -out flag allows you to save the execution plan to a file. This guarantees that the plan 
         generated precisely matches what will be applied later, eliminating any discrepancies that could arise from 
         alterations in configuration or remote resources.}
  4.c. Terraform apply - command executes the actions proposed in a Terraform plan to create, update, or destroy 
       infrastructure
  4.d. Terrafrom destroy -To destroy resurce that created in terrafrom 
       To delete speciific resources we can achive by following command to delete sepcific ec2 istance name 
       aws_instance.demo_vm_1
       
        terraform destroy --target aws_instance.demo_vm_1}

5. Terraform Core concepts:
    1. Provider - 
    2. Resource
    3. variables
    4. Data source
    5. Modules
    6. Provisioners
    7. State file
    8. Backend
    9. remote backend
    10. Secrets/Sesitive information
    11. Workspcae
    12. Locals
    13. Null resources
    14. Dynamic blocks
    15. Conditionals expressions
  1. Provider: To define the specific provider and its settings that Terraform will use to manage and interact with infrastructure resources. We can also giv emulti provider provider at a time also 
     provider "google" {
  project = "acme-app"
  region  = "us-central1"
}

     provider "aws" {
  version = "~> 5.0"
  region  = "us-east-1"
}

provider "azurerm" {
  features {}
}

2. Resource Blocks : In this block we declare a resource of a specific type with a specific local name to exist with the given settings

    resource "aws_instance" "web" {
  ami           = "ami-a1b2c3d4"
  instance_type = "t2.micro"
}

3. Variables : It allow you to customize modules without altering their source code. Instead of hardcoing the values we can dynamically pass the vlaues using variblaes
    varibles are  2 types
   1. Input variables: Arguments are mentioned in input variables
      Argument Types:
      1. Default  - A default value which then makes the variable optional.
      2. Type - This argument specifies what value types are accepted for the variable.
      3. Description- This specifies the input variable's documentation.
      4. validation -A block to define validation rules, usually in addition to type constraints.
      5. Sensitive - Limits Terraform UI output when the variable is used in configuration.
      6. Nullable-  Specify if the variable can be null within the module.
      description: briefly explain the purpose of the variable and what kind of value is expected.
      type: specifies the type of value such as string, number, bool, map, list, etc.
      Type Contraint has below types:
       The type argument in a variable block allows you to restrict the type of value that will be accepted as the value 
      for 
       A variable. If no type constraint is set then a value of any type is accepted.
      1. STRING
      2. NUMBER
      3. BOOL
      4. MAP
      5. STRING
      6. SET
      7. OBJECTS
      8. TUPLE
         The keyword any may be used to indicate that any type is acceptable.
      default: If present, the variable is considered to be optional and if no value is set, the default value is used.
2. Variable Definitions (.tfvars) Files
To set lots of variables, it is more convenient to specify their values in a variable definitions file (with a filename ending in either .tfvars or .tfvars.json) and then specify that file on the command line with -var-file:        
      
