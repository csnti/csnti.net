# This repo automatically deploys to csnti.net

AWS CodePipeline is connected to Github and detects any push to the main branch.<br/>
This allows for Continuous Integration / Continuous Delivery (CI/CD)

AWS CodeBuild starts a linux instance which handles the entire build process using a YAML script.<br/>

Git submodules are cloned by a "machine user" with a private SSH key,<br/>
saved on Parameter Store, in an encrypted state.

Read-access to this SSH key is granted only to CodeBuild by Identity Access Management.<br/>

If the build proccess succeeds, then it saves the contents of the directory to an S3 bucket

