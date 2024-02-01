# webinar

This repository is based on the instructions for creating an OpenShift Pipeline found here:

[Creating CI/CD solutions for applications using OpenShift Pipelines](https://docs.openshift.com/pipelines/1.12/create/creating-applications-with-cicd-pipelines.html)

You can substitute the artifacts used to set up the example program on that page with the artifacts in this repository. The idea is that the pipeline itself is reusable. 

Then use the following command to invoke the pipeline:
```
tkn pipeline start build-and-deploy \
-w name=shared-workspace,volumeClaimTemplateFile=https://raw.githubusercontent.com/hupiper/webinar/main/pipeline/persistent_volume_claim.yaml \
-p deployment-name=webinar-site \
-p git-url=https://github.com/hupiper/webinar-site.git \
-p IMAGE='image-registry.openshift-image-registry.svc:5000/$(context.pipelineRun.namespace)/webinar-site' \
--use-param-defaults
```


The repo for the sample web deployment for the pipeline can be found here:

https://github.com/hupiper/webinar-site