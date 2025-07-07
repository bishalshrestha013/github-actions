# Github actions

For multiple jobs, each job runs on separate machine

all the jobs will be executed in parallel by default, but we can make it run in sequence one after another using
needs keyword
if one job get failed, then all the jobs which have dependency of that job will get skipped

## storing workflow data as artifact

how to upload artifacts from one job and download the artifacts in another job

-> For this we have couple of actions already available

1. Upload a build artifact
2. Downlaod a build artifact
