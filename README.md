# Devops
Basic steps:
1. launch instance
2. create key-value pair and save the .pem file.
3. use the public IP.
4. to login to the ec2 instance: "ssh -i location/to/the/.pem file ubuntu@public IP " (we are using ubuntu because we have created ubuntu machine(ec2)).

# Ways to create an EC2 Instaance:
1. AWS CLI: we have to download AWS CLI in our computer and do aws configure.

note: for reference visit: https://docs.aws.amazon.com/efs/latest/ug/gs-step-one-create-ec2-resources.html
# List Bucket:
> aws s3 ls
# Create Bucket:
> aws s3 mb s3://bucket_name

2. By CFT(CLoud Formation Template): simply we need to copy the script and the service will be created.
Refer: https://github.com/awslabs/aws-cloudformation-templates .

Note: for automation of this processes we can use programming languages like python , python uses Boto3 library.
 Link to the documentation: https://boto3.amazonaws.com/v1/documentation/api/latest/index.html

 # To list all the s3 buckets using boto3:
   
   > import boto3
   > s3 = s3.resource('s3')
   > for bucket in s3.buckets.all():
   >     print(bucket.name)

 !! we can find the scripts for listing ec2 and other services as well, in the boto3 documentation.


 # Linux and Shell Scripting:
 when we do ssh to our running instance which is an Ubuntu machine( in most of the cases )
!! to get the address of the current directory:
 > pwd
 (Present Working Directory)

 # Script to Report the AWS usage in a Project: (AWS Project)
    Cron Job: It refers to performing some activity at particular fixed time.
We can do various tasks like:
1 List S3
2 List EC2
3 List IAM Users
4 List Lambda etc.

    Refer: https://docs.aws.amazon.com/cli/latest/ 
for the commands

script file should start with:
> #!/bin/bash

# Github API Integration:
Search for Github API documentation, we can get the commands and endpoints from there.

by this we can do the following tasks and amany more:

1. List the group of people who has access to the repo.
2. List Issues in the repo.
3. Create an issue etc.

# Git VS Github:

1. Git: 
Git is a distributed version control system (DVCS) that allows developers to track changes in their codebase, collaborate with others, and manage different versions of their projects.

Git enables multiple developers to work on a project simultaneously, keeping track of changes and merging them seamlessly.

2. Github: 
GitHub, on the other hand, is a web-based platform that utilizes Git for version control. It provides additional features and a centralized platform for collaboration.

GitHub allows developers to host their Git repositories online, making it easier to share code, collaborate with others, and manage projects.

It includes features like issue tracking, pull requests, and a web-based interface for easier collaboration.

# Distributed VS Non Distributed Version Controlling Systems:

1. Distributed Version Control System (DVCS):

In a distributed version control system, each user has a complete copy of the entire repository, including its full history. Examples of DVCS include Git, Mercurial, and Bazaar. 
Users can work independently on their local copies, commit changes, and even create branches without needing constant access to a central server.
This decentralization makes it easier for developers to work offline and collaborate more flexibly. It also provides redundancy and mitigates the risk of a single point of failure.

2. Non-Distributed (Centralized) Version Control System:

In a non-distributed or centralized version control system, there is a single, central repository that contains the master copy of the codebase and its history. Examples include CVS (Concurrent Versions System) and Subversion (SVN).
Developers typically check out a working copy from the central repository, make changes, and then commit those changes back to the central repository.
Collaboration often involves interacting with the central server, and working offline or creating branches can be more challenging compared to distributed systems.

# Key Differences:

Collaboration:

In DVCS, collaboration can happen more independently, with each user having a full copy of the repository.
In non-distributed systems, collaboration usually involves interactions with the central server.
Offline Work:

DVCS allows developers to work offline, committing changes locally, and then synchronizing with the central repository later.
Non-distributed systems may require a constant connection to the central server for most operations.
Redundancy:

DVCS inherently provides redundancy because every user has a full copy of the repository.
In non-distributed systems, the central server holds the master copy, and redundancy depends on backup strategies.
Flexibility:

DVCS offers more flexibility for branching and merging, often making these operations faster and more straightforward.
Non-distributed systems can also handle branching and merging but may involve more interaction with the central server.

# Examples:

Distributed: Git, Mercurial, Bazaar
Non-Distributed (Centralized): CVS, Subversion (SVN)

# Git Branching:
Branching in Git is a powerful feature that allows developers to create divergent lines of development within a project. It enables you to work on new features, bug fixes, or experiments without affecting the main codebase until you are ready to merge your changes. Here's an overview of the basic Git branching concepts:

1. Creating a New Branch:

        git branch branch_name

2. Switching to a Branch:

        git checkout branch_name

Alternatively, you can use the following command to create and switch to a new branch in one 

        git checkout -b branch_name

3. List Local Branches:

        git branch

4. List Remote Branches:

        git branch -r

5. List All Branches (Local and Remote):

        git branch -a

6. Merge Changes from One Branch into Another:
First, switch to the branch where you want to merge changes (e.g., the main branch).
    
        git checkout main
Then, merge the changes from another branch.

        git merge branch_name

7. Delete a Branch After Merging:

        git branch -d branch_name

8. Resolving Conflicts:
If there are conflicting changes during a merge, Git will mark the conflicted files. You need to resolve the conflicts manually, then add and commit the changes.

> Example Workflow:

    # Create and switch to a new branch
        git checkout -b feature_branch

    # Make changes and commit them
        git add .
        git commit -m "Implemented new feature"

    # Switch back to the main branch
        git checkout main

    # Merge changes from the feature branch
        git merge feature_branch

    # Delete the feature branch if it's no longer needed
        git branch -d feature_branch

# Feature Branch:
A feature branch is a separate branch in a version control system, often used in Git, where developers work on a specific feature or a set of related features. The purpose of feature branches is to isolate changes associated with a particular feature, bug fix, or enhancement from the main development branch until the work is completed and ready for integration.

# Release Branch:
A release branch is a branch in a version control system, commonly used in Git, that is created to prepare and stabilize a codebase for a software release. The purpose of a release branch is to freeze the development of new features and focus on bug fixes, testing, and other activities that ensure the code is in a stable state for release.

# Master Branch:
The term "master branch" is a convention used in version control systems, especially in Git, to denote the primary or default branch in a repository. The master branch typically represents the main line of development and is considered the stable and production-ready version of the codebase. It serves as the baseline from which other branches, such as feature branches or release branches, may diverge and later merge back into.

# Hot-Fix Branch:
A hotfix branch is a specific type of branch in version control systems, commonly used in Git, that is created to address critical issues or bugs in a production environment. The purpose of a hotfix branch is to allow developers to quickly isolate and fix a problem without disrupting the normal development workflow. Hotfixes are typically used to address issues that need an immediate resolution in a stable version of the software.

Here's a typical workflow involving a hotfix branch:

1. Identify the Critical Issue:
. A critical bug or issue is identified in the current production version of the software that requires an immediate fix.

2. Create a Hotfix Branch:
. A new branch, often named "hotfix" or something similar, is created from the main production branch (e.g., master or main).

        git checkout -b hotfix_branch main

3. Fix the Issue:
. Developers work on the hotfix branch to implement the necessary fix for the identified issue.

        git add .
        git commit -m "Fix critical issue in production"

4. Testing the Hotfix:
. The hotfix branch undergoes testing to ensure that the fix resolves the issue without introducing new problems.

5. Merge into Production:
. Once the hotfix is tested and verified, it is merged into the main production branch.

        git checkout main
        git merge hotfix_branch

6. Tag the Release:

. A version tag is often applied to the main branch to mark the release containing the hotfix.

        git tag -a v1.0.1 -m "Hotfix release 1.0.1"

7. Optional: Merge Changes Back to Development:

. In some workflows, the changes made in the hotfix branch might be merged back into the development branch to ensure that the fixes are part of ongoing development.

        git checkout development
        git merge hotfix_branch

8. Delete Hotfix Branch (Optional):

. After the hotfix is successfully completed and merged, the hotfix branch may be deleted.

        git branch -d hotfix_branch

# Fork VS Clone:

"Fork" and "Clone" are terms commonly used in the context of version control systems, particularly with Git. They refer to different actions and concepts:
Fork:

Usage: Forking is specific to platforms like GitHub, GitLab, and Bitbucket.
Meaning: Forking creates a personal copy of someone else's project (usually a repository on a code hosting platform).
Purpose: It is often used when you want to contribute to someone else's project or use it as a starting point for your own project.
Result: After forking, you have your own copy of the repository on your GitHub/GitLab/Bitbucket account.

Steps:

Visit the repository on the code hosting platform.
Click the "Fork" button.
You now have a copy of the repository under your account.
Clone:

Usage: Cloning is a Git operation.
Meaning: Cloning creates a local copy of a repository on your own machine.
Purpose: It is done when you want to work on the code locally, make changes, and push those changes back to the remote repository.
Result: After cloning, you have the repository files on your local machine.

Steps:

Open a terminal.
Use the git clone command followed by the URL of the repository.
Example: git clone https://github.com/username/repository.git
This creates a local copy of the repository on your machine.
In summary:

Forking is a remote operation on a code hosting platform, creating a personal copy on the platform itself.
Cloning is a local operation using Git, creating a copy on your own machine.

# Git Merge VS Rebase:

1. Merge:

Usage: Merging is a straightforward way to integrate changes from one branch into another.
Process: When you merge a branch, Git creates a new commit that combines the changes of the merged branch with the target branch.
Result: The branch history becomes a series of commits, and there is a merge commit that represents the integration point.

Example:
        # Switch to the target branch
        git checkout target_branch

        # Merge changes from the source branch
        git merge source_branch
Pros:

Simple and easy to understand.
Preserves the original branch history.

Cons:

Creates additional merge commit(s), which can clutter the history.

2. Rebase:

Usage: Rebasing is a way to integrate changes by moving or combining a sequence of commits to a new base commit.
Process: Git temporarily stashes the changes in the target branch, applies the commits from the source branch one by one, and then reapplies the stashed changes.
Result: The branch history appears linear, as if the changes from the source branch were made directly on top of the target branch.

Example:
        # Switch to the source branch
        git checkout source_branch

        # Rebase changes onto the target branch
        git rebase target_branch

Pros:

Results in a cleaner and more linear history.
Avoids unnecessary merge commits.

Cons:

Rewrites commit history, which can cause issues if changes have already been pushed to a shared repository.

Choosing Between Merge and Rebase:

Use Merge:

For public/shared branches where commit history is important.
When working on a feature branch that will be merged into the main branch.
Use Rebase:

For local/private branches to maintain a clean and linear history.
When preparing a feature branch for integration into the main branch.

Note: It's generally not recommended to rebase commits that have been pushed to a shared repository, as it can cause confusion and synchronization issues for collaborators.

# Configuration Management:
Configuration management in DevOps is a crucial aspect that involves the process of handling changes systematically to a system's configuration, ensuring consistency and traceability across various environments. This helps in reducing errors, enhancing collaboration, and maintaining the stability of software applications. Here are key components and practices related to configuration management in DevOps:

1. Infrastructure as Code (IaC):
   - Definition: Infrastructure as Code is a key concept where infrastructure configurations are expressed in a machine-readable script.
   - Benefits: Enables automated and consistent provisioning of infrastructure, reduces manual errors, and provides version control for infrastructure changes.

2. Version Control Systems (VCS):
   - Definition: Version control systems like Git are used to manage changes to source code, configurations, and other artifacts.
   - Benefits: Facilitates collaboration, tracks changes, and provides a history of configurations. Enables rollbacks and parallel development.

3. Continuous Integration (CI):
   - Definition: CI involves automatically integrating code changes from multiple contributors into a shared repository.
   - Benefits: Ensures that code changes are regularly integrated and tested, reducing integration issues. This practice helps catch and fix problems early in the development process.

4. Continuous Deployment (CD):
   - Definition: CD automates the deployment of applications to various environments after successful CI.
   - Benefits: Enhances the speed and frequency of releases while maintaining consistency and reliability. Automated deployments reduce the risk of human errors.

5. Configuration Drift Prevention:
   - Definition: Configuration drift occurs when configurations in different environments deviate from the intended state.
   - Mitigation: Regularly validate and enforce configurations across environments to prevent drift. Tools like Puppet, Chef, or Ansible can be used to enforce desired states.

6. Configuration Auditing:
   - Definition: Regularly audit configurations to ensure compliance with security and regulatory requirements.
   - Benefits: Helps identify and rectify non-compliance issues early, reducing security risks and ensuring adherence to organizational policies.

7. Environment-specific Configurations:
   - Definition: Maintain separate configuration files for different environments (development, testing, staging, production).
   - Benefits: Avoids hardcoding environment-specific values, making it easier to manage and deploy applications across different stages of the development lifecycle.

8. Secrets Management:
   - Definition: Securely manage sensitive information such as API keys, passwords, and certificates.
   - Best Practices: Use tools like HashiCorp Vault, AWS Secrets Manager, or Azure Key Vault to store and manage secrets securely. Avoid storing sensitive information in code repositories.

9. Change Management and Documentation:
   - Definition: Document and track changes to configurations, including the reasons for changes.
   - Benefits: Facilitates collaboration, helps in troubleshooting, and provides a historical record of changes.

10. Monitoring and Alerting:
   - Definition: Implement monitoring to detect anomalies or issues related to configurations.
   - Benefits: Early detection of configuration-related problems allows for timely resolution, ensuring system stability.

By integrating these practices into your DevOps processes, you can establish a robust configuration management system that promotes collaboration, automation, and consistency across development, testing, and production environments.

# Tools Used for Configuration Management:
There are several tools available for implementing configuration management in a DevOps environment. Each tool has its strengths and is often chosen based on the specific needs and preferences of the organization. Here are some popular configuration management tools:

1. Ansible:
   - Description: Ansible is an open-source automation tool that uses simple, human-readable YAML scripts to define configurations.
   - Key Features:
     - Agentless architecture.
     - Large community and extensive module library.
     - Supports push-based configuration management.
     - Follows Push Model

2. Puppet:
   - Description: Puppet is a declarative configuration management tool that uses a custom language (Puppet DSL) to define configurations.
   - Key Features:
     - Agent-based architecture.
     - Provides a rich set of modules.
     - Supports both Windows and Unix-like systems.
     - Follows Pull Model

3. Chef:
   - Description: Chef is a configuration management tool that uses a Ruby-based DSL (Domain-Specific Language) to define configurations.
   - Key Features:
     - Uses a client-server architecture.
     - Emphasizes infrastructure as code.
     - Well-suited for managing complex infrastructures.

4. SaltStack:
   - Description: SaltStack, or Salt, is an open-source configuration management and remote execution tool.
   - Key Features:
     - Agent-based architecture.
     - Fast and scalable.
     - Uses a Python-based configuration language.

5. Terraform:
   - Description: Terraform is an open-source Infrastructure as Code (IaC) tool for building, changing, and versioning infrastructure.
   - Key Features:
     - Declarative configuration language (HCL - HashiCorp Configuration Language).
     - Supports multiple cloud providers and on-premises infrastructure.
     - Focuses on provisioning and orchestration.

6. Docker:
   - Description: Docker is a platform for automating the deployment, scaling, and management of applications using containers.
   - Key Features:
     - Containers encapsulate applications and their dependencies.
     - Simplifies application deployment and scaling.
     - Works well with orchestration tools like Kubernetes.

7. Kubernetes:
   - Description: Kubernetes is an open-source container orchestration platform for automating the deployment, scaling, and management of containerized applications.
   - Key Features:
     - Manages containerized applications across clusters of machines.
     - Provides declarative configuration.
     - Offers automated scaling and self-healing.

8. HashiCorp Vault:
   - Description: HashiCorp Vault is a tool for managing secrets and protecting sensitive data.
   - Key Features:
     - Centralized secret management.
     - Dynamic secrets generation.
     - Integration with various authentication systems.

9. AWS CloudFormation:
   - Description: AWS CloudFormation is an IaC service provided by Amazon Web Services for defining and provisioning AWS infrastructure.
   - Key Features:
     - Uses JSON or YAML templates to describe resources.
     - Supports a wide range of AWS services.
     - Simplifies the deployment and management of AWS resources.

10. Jenkins:
    - Description: Jenkins is an open-source automation server that facilitates building, testing, and deploying code.
    - Key Features:
      - Extensive plugin support.
      - Integrates with version control systems and configuration management tools.
      - Supports continuous integration and continuous delivery (CI/CD) pipelines.

When selecting a configuration management tool or tools for your DevOps workflow, consider factors such as the complexity of your infrastructure, the skills of your team, and the specific requirements of your project. It's common for organizations to use a combination of these tools to address different aspects of configuration management and automation.

# We will move forward with Ansible:
1. Ansible is an open-source IT automation platform that automates provisioning, configuration management, application deployment, orchestration, and many other IT processes. It is agentless, meaning it does not require any software to be installed on the managed systems.

Ansible uses a simple YAML language to define playbooks, which are blueprints of automation tasks. Playbooks can be used to automate a wide variety of tasks, including:

- Installing and configuring software
- Managing files and directories
- Creating and managing users and groups
- Starting and stopping services
- Deploying applications
- Orchestrating complex workflows

Ansible is a powerful and flexible tool that can be used to automate a wide variety of IT tasks. It is a popular choice for organizations that are looking to improve their operational efficiency and reduce their costs.

Here are some of the benefits of using Ansible:

- Simple to use: Ansible uses a simple YAML language that is easy to learn, even for those who are not familiar with programming.
- Agentless: Ansible does not require any software to be installed on the managed systems, which makes it easy to deploy and manage.
- Flexible: Ansible can be used to automate a wide variety of tasks, making it a versatile tool for IT professionals.
- Open source: Ansible is an open-source tool, which means that it is free to use and there is a large community of users and developers who can provide support.

If you are looking for an easy-to-use and powerful IT automation tool, Ansible is a great option to consider.
Here are some additional resources that you may find helpful:

- Ansible documentation: https://docs.ansible.com/
- Ansible Galaxy: https://galaxy.ansible.com/
- Ansible community: https://github.com/jamielinux/ansible-discourse.

# How we can achieve Agentless(assword less) Authenticaation using Ansible:

- Doing this needs 2 or more than 2 ec2 instances.
- Let's say we hhave 2 two instances one is ansible-server and second one is the Target-server.

- we have to install ansible on this servers (ec2 innstances)
- Refer:
         https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-and-upgrading-ansible
- Create ssh key by running: `ssh-keygen` (in both the servers)
- Copy the id_rsa.pub from the ansible-server and paste it to the authorized-key file in the target server (this file is created by the ssh-keygen command only)
- Create inventory file in the ansible server and paste the private ipv4 address of the target server in it.
- Thats all now if you will try running `ssh <private-ip-address-of-target-server>` you will be able to communicate it with agentlessly. 
- we can use Ansible adhoc commands to perfrom the tasks on the target servers.
- for example: `ansible -i inventory all -m "shell" -a "touch devops-file` (run this command on the ansible server and it will create a file called devops-file on the target server)
- Refer: https://docs.ansible.com/ansible/latest/command_guide/intro_adhoc.html

# Managing different number of servers in Inventory file:

INI Format:

        [web_servers]
        web1 ansible_host=192.168.1.101
        web2 ansible_host=192.168.1.102

        [database_servers]
        db1 ansible_host=192.168.1.201
        db2 ansible_host=192.168.1.202
and many other ways are there.

# Test Connectivity of the servers:
         ansible -i inventory.ini -m ping web_servers

         ansible -i inventory.ini -m ping database_servers

- It will return:

        web1 | SUCCESS => {
        "ansible_facts": {
                "discovered_interpreter_python": "/usr/bin/python3"
        },
        "changed": false,
        "ping": "pong"
        }

        web2 | SUCCESS => {
        "ansible_facts": {
                "discovered_interpreter_python": "/usr/bin/python3"
        },
        "changed": false,
        "ping": "pong"
        }

# Ansible Playbook:
An Ansible playbook is a script written in YAML format that defines a set of tasks to be executed on remote hosts. Playbooks are at the heart of Ansible's configuration management and automation capabilities. They allow you to define the desired state of systems and execute a series of tasks to achieve that state. Playbooks are idempotent, meaning you can run them multiple times without changing the end result.

Here are key components and concepts related to Ansible playbooks:

### 1. **YAML Format:**
   - Playbooks are written in YAML (YAML Ain't Markup Language) format, which is a human-readable data serialization format. YAML is easy to read and write and is used to define the structure of playbooks.

### 2. **Structure:**
   - Playbooks consist of a set of plays, and each play is a set of tasks. A play is essentially a scenario or a set of operations that should be performed on a specific set of hosts.

### 3. **Plays:**
   - A play is a unit of organization in a playbook. It defines a set of tasks and the hosts on which those tasks should be executed. A playbook can have one or more plays.

### 4. **Tasks:**
   - Tasks are the individual units of work within a play. Each task typically corresponds to a specific action or operation, such as installing a package, copying a file, or restarting a service.

### 5. **Hosts:**
   - Hosts are the target machines or nodes on which the tasks specified in the playbook will be executed. You can define hosts explicitly in the playbook or refer to groups of hosts from an inventory file.

### 6. **Modules:**
   - Tasks use Ansible modules to perform specific actions. Modules are small pieces of code that Ansible executes on the target hosts. Examples of modules include the `yum` module for package management and the `file` module for managing files.

### 7. **Variables:**
   - Playbooks can use variables to make them more flexible and reusable. Variables can be defined at different levels, such as at the playbook level, play level, or task level, and they can be overridden based on conditions.

### 8. **Handlers:**
   - Handlers are tasks that are only run if a particular task reports a change. They are typically used to restart services or perform other actions triggered by changes in the system.

### Example Playbook:

Here's a simple example of an Ansible playbook:

```yaml(format) "the --- indicates that it is an YAML file".
---
- name: Install and configure web server
  hosts: web_servers
  become: true

  tasks:
    - name: Update package cache
      package:
        name: "{{ item }}"
        state: latest
      with_items:
        - nginx
        - apache2

    - name: Copy configuration file
      copy:
        src: files/nginx.conf
        dest: /etc/nginx/nginx.conf
      notify: Restart Nginx

  handlers:
    - name: Restart Nginx
      service:
        name: nginx
        state: restarted
```
Second Example:
``` 
--- 
- name: Install and Start Nginx
  hosts: all
  become: true

  tasks:
   - name: Install Nginx
     apt: 
        name: nginx
        state: present
   - name: Start nginx
     service: 
        name: nginx
        state: started     

In this example:

- The playbook installs or updates the Nginx and Apache packages.
- It copies an Nginx configuration file to the target hosts.
- It includes a handler to restart the Nginx service when the configuration changes.

To run the playbook, you would use the `ansible-playbook` command:

```bash
ansible-playbook -i inventory.ini web_server_playbook.yml
```

This is a simple illustration, and real-world playbooks can include more complexity, conditionals, loops, and integration with variables and roles. Playbooks are a powerful tool for orchestrating complex automation tasks in IT environments.

# Ansible Roles:
In Ansible, roles are a way to organize and structure your playbooks in a more modular and reusable manner. Roles provide a higher level of abstraction and help break down complex automation tasks into smaller, manageable components. Roles are essentially a collection of tasks, variables, handlers, and other resources grouped together for a specific purpose.

Key features and components of Ansible roles include:

### 1. **Directory Structure:**
   - Ansible roles have a specific directory structure that includes subdirectories for tasks, handlers, templates, and other related files. The standardized structure makes it easy to organize and share roles.

### 2. **Reusable Components:**
   - Roles encapsulate reusable components such as tasks, variables, and handlers. This makes it easier to share and reuse automation logic across different playbooks or projects.

### 3. **Tasks:**
   - The `tasks` directory within a role contains YAML files defining the tasks to be executed. Tasks describe the actions to be performed on the target hosts.

### 4. **Handlers:**
   - The `handlers` directory contains YAML files with tasks that are only executed if notified by other tasks. Handlers are typically used for actions like restarting services or performing other tasks triggered by changes.

### 5. **Templates:**
   - The `templates` directory can contain Jinja2 template files used to generate configuration files dynamically. This allows for the creation of flexible and customized configuration files.

### 6. **Defaults:**
   - The `defaults` directory includes YAML files defining default variable values for the role. These values can be overridden by users in their playbooks.

### 7. **Vars:**
   - The `vars` directory allows you to define additional variables specific to the role. These variables can be used within the role's tasks.

### 8. **Meta:**
   - The `meta` directory can include metadata about the role, such as dependencies on other roles, supported platforms, and other information.

### 9. **Roles in Playbooks:**
   - In a playbook, you can use the `roles` keyword to include one or more roles. This simplifies the playbook structure and allows for the reuse of roles across different playbooks.

### Example Role Directory Structure:

Here's an example directory structure for an Ansible role:

```
my_role/
|-- tasks/
|   |-- main.yml
|-- handlers/
|   |-- main.yml
|-- templates/
|   |-- config.j2
|-- defaults/
|   |-- main.yml
|-- vars/
|   |-- main.yml
|-- meta/
|   |-- main.yml
```

### Example Playbook with Roles:

```yaml
---
- name: My Playbook with Roles
  hosts: my_servers
  roles:
    - my_role
```

In this example, the `my_role` directory structure aligns with the standard role structure, and the role is included in the playbook using the `roles` keyword.

Roles are a powerful feature in Ansible, enabling better organization, reusability, and maintainability of automation code. They are particularly useful for managing complex infrastructure configurations and deploying applications consistently across different environments.

# To create a role:

1. Make a new directory called roles.
2. Switch to that directory and run :

         ansible-galaxy role init <role-name>
3. this will create a role in your roles directory, try checking it with `ls` command.

For Examples visit: https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbEFvUEx5MXBja0cxTHV5LUhQT2lDaXd0dEFId3xBQ3Jtc0trUXdiUzJuZ0o2cmxjN2FzbXJhSndCWFQtZ3pnYlFRaGtCeHNEREF3eE5sOUI1NkZtbFdvS1hMUkw4cmFtVXJHbV82YmNwNzZfcWVVejlUQ0Z3U1RROE10NUhuSXdLMkpQby0xVGJ5SkhMNDQ2U2lOTQ&q=https%3A%2F%2Fgithub.com%2Fansible%2Fansible-examples&v=Z6T2r3Xhk5k

# Infrastructure as Code (IaC):
Infrastructure as Code (IaC) is a concept and practice that involves managing and provisioning computing infrastructure through machine-readable script files, rather than through physical hardware configuration or interactive configuration tools. The goal of IaC is to automate and standardize the process of setting up and managing infrastructure, making it more scalable, repeatable, and less error-prone. Here are key aspects of Infrastructure as Code:

### 1. **Automation:**
   - IaC relies on automation tools and scripts to define and deploy infrastructure. This can include servers, networks, storage, and other infrastructure components.

### 2. **Declarative vs. Imperative:**
   - Declarative IaC involves describing the desired end state of the infrastructure without specifying the step-by-step process. Imperative IaC involves specifying the exact steps to achieve the desired state.

### 3. **Version Control:**
   - IaC scripts are typically stored in version control systems (e.g., Git). This allows for versioning, history tracking, and collaboration among team members.

### 4. **Repeatable and Consistent:**
   - IaC allows infrastructure to be provisioned, modified, and decommissioned in a consistent and repeatable manner. This reduces the likelihood of errors and ensures that different environments remain consistent.

### 5. **Scalability:**
   - IaC enables the easy scaling of infrastructure by defining the desired state and allowing automation tools to handle the provisioning of additional resources.

### 6. **Reusability:**
   - IaC scripts can be reused across different environments or projects. This reuse reduces duplication of effort and promotes consistency across various deployments.

### 7. **Documentation:**
   - IaC serves as a form of documentation. By examining the IaC scripts, users can understand how the infrastructure is configured and provisioned.

### 8. **Collaboration:**
   - IaC facilitates collaboration between development and operations teams. Both teams can work on the infrastructure code, allowing for a DevOps approach to managing IT environments.

### 9. **Popular IaC Tools:**
   - Several tools are commonly used for implementing Infrastructure as Code. Some popular examples include:
     - **Terraform:** A declarative IaC tool that supports multiple cloud providers and on-premises infrastructure.
     - **Ansible:** An imperative IaC tool that automates configuration management, application deployment, and other tasks.
     - **Chef:** An imperative IaC tool that automates infrastructure configuration and management.
     - **Puppet:** A declarative IaC tool that automates configuration management and system administration tasks.

### 10. **Cloud Orchestration:**
   - IaC is closely associated with cloud computing, where infrastructure resources can be provisioned and managed programmatically. Cloud providers often offer native IaC solutions or integrations with popular IaC tools.

Adopting Infrastructure as Code practices can lead to more efficient, reliable, and scalable management of IT infrastructure, whether on-premises or in the cloud. It aligns with modern DevOps practices and contributes to the overall agility and stability of an organization's technology stack.

# Terraform:

Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp. It enables users to define and provision infrastructure resources in a declarative configuration language. Terraform supports various cloud providers, as well as on-premises and third-party services, allowing users to manage and orchestrate their infrastructure across diverse environments.

Key features and concepts of Terraform include:

### 1. **Declarative Configuration:**
   - Terraform uses a declarative language to define the desired state of infrastructure. Users specify what resources they want, and Terraform figures out how to create, modify, or delete those resources to achieve the desired state.

### 2. **Providers:**
   - Terraform uses providers to interact with different infrastructure platforms. Providers are plugins that enable Terraform to manage resources in specific environments, such as AWS, Azure, Google Cloud, and more.

### 3. **Resource Definitions:**
   - Infrastructure resources, such as virtual machines, networks, databases, and other components, are defined using Terraform configuration files. These files use HashiCorp Configuration Language (HCL) syntax.

### 4. **State Management:**
   - Terraform maintains a state file that records the current state of the managed infrastructure. This state is used to plan and apply changes, ensuring that Terraform can accurately track the state of the infrastructure over time.

### 5. **Plan and Apply Workflow:**
   - Terraform follows a two-step process: `terraform plan` and `terraform apply`. The plan phase shows what changes will be made to the infrastructure, and the apply phase executes those changes.

### 6. **Modules:**
   - Terraform allows users to organize configurations into reusable modules. Modules enable the encapsulation and reuse of infrastructure code, promoting a modular and scalable approach to IaC.

### 7. **Variables and Outputs:**
   - Terraform configurations support variables to parameterize configurations, making them more flexible. Outputs allow users to expose certain values from the infrastructure for reference or use in other configurations.

### 8. **Remote Backends:**
   - Terraform supports remote backends for storing the state file. This enables collaboration among team members working on the same infrastructure, and it provides additional features like locking to prevent concurrent modifications.

### 9. **Community and Ecosystem:**
   - Terraform has a large and active community. The HashiCorp Registry contains a vast collection of modules and configurations shared by the community, making it easier to adopt best practices and leverage pre-built solutions.

### 10. **Multi-Cloud and Hybrid Cloud Support:**
   - Terraform is not tied to a specific cloud provider. It supports multi-cloud and hybrid cloud scenarios, allowing users to manage resources across different environments using a single configuration.

### Example Terraform Configuration:

```hcl
provider "aws" {
  region = "us-west-2"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

In this example:

- The configuration uses the AWS provider to interact with Amazon Web Services (AWS).
- It defines an AWS EC2 instance with a specific Amazon Machine Image (AMI) and instance type.

### Getting Started:

1. **Installation:**
   - Install Terraform on your local machine by downloading the binary from the [official Terraform website](https://www.terraform.io/downloads.html) or using a package manager. or https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli

2. **Configuration:**
   - Create a Terraform configuration file (typically with a `.tf` extension) and define the desired infrastructure.

3. **Initialization:**
   - Run `terraform init` to initialize the working directory. This downloads the necessary providers and sets up the backend.

4. **Planning:**
   - Run `terraform plan` to see what changes will be made to the infrastructure.

5. **Application:**
   - If satisfied with the plan, run `terraform apply` to apply the changes and create or modify the infrastructure.

Terraform has become a widely adopted tool in the DevOps and cloud computing communities for managing infrastructure efficiently and consistently. It provides a flexible and extensible framework for automating infrastructure provisioning and configuration.

For Commands and Reference: https://registry.terraform.io/providers/hashicorp/aws/latest/docs
