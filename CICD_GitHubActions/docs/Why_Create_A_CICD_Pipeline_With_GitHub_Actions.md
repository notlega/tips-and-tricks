# Why create a CI/CD pipeline with GitHub Actions

GitHub Actions automates most of the manual processes like tests and builds.

GitHub Actions will also perform the actions much faster than performing them manually.

For the examples below, I will be using a NextJS web application.

## Performing the build, tests and hosting manually

When a pull request has been made to the main branch, developers will have to manually build, test and host the application.

To do so, they would have to pull the branch from remote to local and run the commands manually.

This would be slow and inefficient as the time taken for pulling, building, testing and reviewing could have been used for other tasks.

When the pull request is finally accepted and pulled into the develop branch, it would have to be redeployed.

This requires the developer to open the Vercel website, login and reselect the repository that they want to redeploy.

The developer would waste a fair bit of time waiting for the website to load and properly make sure that the application has been deployed successfully.

This will take a fair bit of time that can be reduced by creating a CI/CD pipeline on GitHub Actions to automate deployment.

## Performing the build, tests and hosting using a pipeline

With various CI/CD pipelines using GitHub Actions, we can optimise the developer experience.

When a pull request is made to the main branch, various pipelines for building and testing code will start.

When both build and tests have passed, the pull request will automatically be merged into the main branch.

After the pull request has been merged, the deployment pipeline will start and automatically deploy the application onto Vercel.

The status of the deployment can be seen easily on the home page of the application next to the latest commit message.

This will allow developers to save time and have more time to code instead.

## Previous Topic

[What is GitHub Actions](./What_Is_GitHub_Actions.md)

## Next Topic

[Basics of YAML](./Basics_of_YAML.md)
