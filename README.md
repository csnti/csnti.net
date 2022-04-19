# This repo is a staging area for csnti.net

AWS CodePipeline is connected to Github and detects any push to the main branch.

AWS CodeBuild starts a linux instance which handles the entire build process using a Yaml script.

Git submodules are cloned by a "machine user" with a private SSH key 
that's saved and encrypted on Parameter Store. This allows private repos to be deployed.

Read-access to this SSH key is granted to CodeBuild using AWS Identity Access Management
(no one's getting hacked today 😎).
