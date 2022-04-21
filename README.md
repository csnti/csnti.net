# This repo automatically deploys to csnti.net

AWS CodePipeline is connected to Github and detects any push to the main branch.<br/>
This allows for Continuous Integration / Continuous Delivery (CI/CD).

AWS CodeBuild starts a linux instance which handles the entire build process using a YAML script.<br/>

Git submodules are cloned by a "machine user" with a private SSH key,<br/>
saved on Parameter Store, in an encrypted state.

Read-access to this SSH key is granted only to CodeBuild by Identity and Access Management.<br/>

If the build proccess succeeds, then it saves the contents of the directory to an S3 bucket.<br/>
Usually deployment takes about 10-15 minutes to complete.<br/>
<br/>
<br/>
<br/>
<br/>
As of now, I have to invalidate CloudFront files manually with /* <br/>

The next feature that I'd like to integrate into CodePipeline<br/>
is a Lambda function that handles CloudFront invalidations right after deployment.<br/>
I'll be doing this later though, it's not a huge priority right now.
