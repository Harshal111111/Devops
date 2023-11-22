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


# TRying to add code block



