# Github actions

For multiple jobs, each job runs on separate machine

all the jobs will be executed in parallel by default, but we can make it run in sequence one after another using
needs keyword
if one job get failed, then all the jobs which have dependency of that job will get skipped

## storing workflow data as artifact

how to upload artifacts from one job and download the artifacts in another job

-> For this we have couple of actions already available

1. Upload a build artifact
2. Download a build artifact

NOTE:
If we use this upload a build artifact, the artifact will be available for download and by default it will be stored for 90 days by default and max. size we can store is 500MB for free account
you can change this by: settings/actions/general (artifact and log retention)

## working with variables in different levels

In workflows we have an option to store environment variables which could be like non-sensitive configuration values like username, some flags or other values which are used for the application. Environment variables can be stored in 3 different places:
It can be stored at

1. Step level (env defined are available to that particular step only)
2. Job level (env defined are available to all the steps)
3. Workflow level (env defined are available to all the jobs)

syntax:

env:
CONTAINER_REGISTRY: docker.io (key value format)
DOCKER_USERNAME: johndoe

we can access these env variable in commands using:

- $CONTAINER_REGISTRY
- ${{ env.CONTAINER_REGISTRY }}

## Working with repository level secrets

In order to securely store the sensitive value, we have multiple options.

we can store the secret at the organization level. So we can create organizations and we can store secrets and environment variables which will be used by all the workflows which are part of that organization or we can use them at the repository level or at the environment level

### Repository level secrets

Define secrets inside:
`settings/secrets and variable/actions`

accessing secrets variable:
${{ secrets.DOCKER_PASSWORD }}

accessing the repository or the organization or the environment level variables, syntax:
${{ vars.DOCKER_USERNAME }}
