Learning Pool static website task 
Lukasz Hazy
Different AWS solutions for hosting static website:


S3 static website with Cloudfront as CDN.
All files developed locally being pushed to github dev branch and then merged into master branch with authorised pull requests. Every change triggers codepipeline action to update the stack.
Whole infrastructure developed as IaC using 2 Cloudformation stacks:

Pipeline.yaml which creates pipeline which then uses Bucket-web.yaml which creates below resources during Deploy-Infra stage of previously created pipeline which is triggered using github webhook.




	

S3
Scalability as it is practically unlimited storage which is adjusting to requirements without any further activity needed and pay for what you use feature. Use costs mentioned at the beginning of the document. 
No public access and the only allowed access is through cloudfront distribution providing security.
Versioning enabled for disaster recovery and safety.
Encryption enabled for safety

Cloudfront 
Reduce latency by delivering data through 310+ globally dispersed Points of Presence (PoPs) with automated network mapping and intelligent routing.
Improve security with traffic encryption and access controls, and use AWS Shield Standard to defend against DDoS attacks at no additional charge.
Cut costs with consolidated requests, customizable pricing options, and zero fees for data transfer out from AWS origins.

Pipeline
fully managed continuous delivery service that helps automate release pipelines for fast and reliable application and infrastructure updates.
automates the build, test, and deploy phases of release process every time there is a code change
Integrated with github through github webhook 


Github
Two branches: dev and master. All changes made locally are being pushed into dev branch and then merged with master branch using pull requests upon approval.
Authorisation token used for connection to AWS services.




Additional manual approval stage can be added to the pipeline before deploy-web stage giving additional safety/ testing feature before changes are applied to the production.
Also another stage with creating dev bucket can be added and url for it provided within the manual approval stage for testing. Also developing new features within dev branch and merging upon approval provide above as well before it’s even picked up by the pipeline.

Also s3 cross region replication available if required for availability purposes.

Files kept locally and within github and also whole infrastructure as a code provide relatively short time of retrieval.  






