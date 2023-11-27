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
