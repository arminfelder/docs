---
title:  Pipelines
weight: 3700
---
# Pipelines

## Enabling CI Pipelines

1. Select cluster from drop down.

2. Under tools menu select pipelines.

3. Follow instructions for setting up github auth on page.


## Creating CI Pipelines

1. Go to the project you want this pipeline to run in.

2. Select workloads from the top level Nav bar

3. Select pipelines from from the secondary Nav bar

4. Click Add pipeline button.

5. Enter in your repository name (Autocomplete should help zero in on it quickly).

6. Select Branch options.

	-	Only the branch {BRANCH NAME}: Only events triggered by changes to this branch will be built.

	-	Evertyhing but {BRANCH NAME}: Build any branch that triggered an event EXCEPT events from this branch.

	-	All branches: Regardless of the branch that triggered the event always build.

	>**Note:** If you want one path for master, but another for PRs or development/test/feature branches, create two separate pipelines.

7. Select the build trigger events. By default, builds will only happen by manually clicking build now in Rancher UI.

	- Automatically build this pipeline whenever there is a git commit. (This respects the branch selection above)

	- Automatically build this pipeline whenever there is a new PR.

	- Automatically build the pipeline. (Allows you to configure scheduled builds similar to Cron)

8. Click Add button.

	By default, Rancher provides a three stage pipeline for you. It consists of a build stage where you would compile, unit test, and scan code. The publish stage has a single step to publish a docker image.


8. Add a name to the pipeline in order to complete adding a pipeline.

9. Click on the ‘run a script’ box under the ‘Build’ stage.

	Here you can set the image, or select from pre-packaged envs.

10. Configure a shell script to run inside the container when building.

11. Click Save to persist the changes.

12. Click the “publish an image’ box under the “Publish” stage.

13. Set the location of the Dockerfile. By default it looks in the root of the workspace. Instead, set the build context for building the image relative to the root of the workspace.

14. Set the image information.

	The registry is the remote registry URL. It is defaulted to Docker hub.
	Repository is the `<org>/<repo>` in the repository.

15. Select the Tag. You can hard code a tag like ‘latest’ or select from a list of available variables.

16. If this is the first time using this registry, you can add the username/password for pushing the image. You must click save for the registry credentials AND also save for the modal.




## Creating a New Stage

1. To add a new stage the user must click the ‘add a new stage’ link in either create or edit mode of the pipeline view.

2. Provide a name for the stage.

3. Click save.


## Creating a New Step

1. Go to create / edit mode of the pipeline.

2. Click “Add Step” button in the stage that you would like to add a step in.

3. Fill out the form as detailed above


## Environment Variables

For your convenience the following environment variables are available in your build steps:

Variable Name           | Description
------------------------|------------------------------------------------------------
CICD_GIT_REPO_NAME      | Repository Name (Stripped of Github Organization)
CICD_PIPELINE_NAME      | Name of the pipeline
CICD_GIT_BRANCH         | Git branch of this event
CICD_TRIGGER_TYPE       | Event that triggered the build
CICD_PIPELINE_ID        | Rancher ID for the pipeline
CICD_GIT_URL            | URL of the Git repository
CICD_EXECUTION_SEQUENCE | Build number of the pipeline
CICD_EXECUTION_ID       | Combination of {CICD_PIPELINE_ID}-{CICD_EXECUTION_SEQUENCE}
CICD_GIT_COMMIT         | Git commit ID being executed.
<!--### Adding a Build Script

Coming Soon

### Publishing an Image

Coming Soon-->

## Importing a Pipeline From YAML

If there is a ##YAML FILE### already checked into the github repository click import.
