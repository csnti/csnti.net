# This repo automatically deploys to csnti.net

AWS CodePipeline is connected to Github and detects any push to the main branch.\ 
This allows for Continuous Integration / Continuous Delivery (CI/CD)

AWS CodeBuild starts a linux instance which handles the entire build process using a YAML script.\

Git submodules are cloned by a "machine user" with a private SSH key,\
saved on Parameter Store, in an encrypted state.

Read-access to this SSH key is granted only to CodeBuild by Identity Access Management.\

If the build proccess succeeds, then it saves the contents of the directory to an S3 bucket

