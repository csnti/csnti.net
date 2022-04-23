# This repo automatically deploys to csnti.net

AWS CodePipeline is connected to Github and detects any push to the main branch.<br/>
This allows for Continuous Integration / Continuous Delivery (CI/CD).

AWS CodeBuild starts a linux instance which handles the entire build process using a YAML script.<br/>

Git submodules are cloned by a "machine user" with a private SSH key,<br/>
saved on Parameter Store, in an encrypted state.

Read-access to this SSH key is granted only to CodeBuild by Identity and Access Management.<br/>

If the build proccess succeeds, then it saves the contents of the directory to an S3 bucket.<br/>
Usually deployment takes about 10-15 minutes to complete (at this scale).<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
A̶s̶ ̶o̶f̶ ̶n̶o̶w̶,̶ ̶I̶ ̶h̶a̶v̶e̶ ̶t̶o̶ ̶i̶n̶v̶a̶l̶i̶d̶a̶t̶e̶ ̶C̶l̶o̶u̶d̶F̶r̶o̶n̶t̶ ̶f̶i̶l̶e̶s̶ ̶m̶a̶n̶u̶a̶l̶l̶y̶ ̶w̶i̶t̶h̶ ̶/̶*̶ <br/>
It seems that CloudFront instantly invalidated (updated its CDN to the S3 bucket)<br/>
after my most-recent deployment, without me having to do anything.<br/>
That's pretty convenient. I'll keep an eye on it in future updates.
