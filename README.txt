1.test the code merge to master
2.take the code put in on aws
3.new image, create new instances, terminate old 
## Summary

Created working development, testing and production environment and built a pipeline to move the code through them using Jenkins.

## Tools
Vagrant, Chef, Jenkins, Python, Packer

## Notes
Python cookbook stored in a github repo ( separate ) with Jenkins pipeline.
github repo >https://github.com/zaidiqbal007/python_cookbook.git/
Jenkins test pipeline > zaid-iqbal-eng47-chefci-cookbook
Jenkins merge to master > zaid-iqbal-eng47-chefci-cookbook-merge-upstream

Python App test > zaid-iqbal-eng47-chefci-app

Forked ItJobsWatch application repo with Vagrantfile, Berksfile, packer.json and ability to simply Vagrant up and run in development.
>https://github.com/zaidiqbal007/ItJobsWatch_app

Jenkins Job that runs test suite on pushes to master branch of forked application repo.

Separate Jenkins job that builds an application AMI using packer.json when tests pass successfully.