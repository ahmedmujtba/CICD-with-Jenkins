# How to push your code from main to production (ec2)

You need to have an ec2 instance with the app running for this task.

1. Setup another Jenkins project, you can follow the guide [here](./README.md), you'll need to add some aditional configuration as follows:

- In `Source Code Management`, you would need to select `none` for this job, this is because our github branches have already been merged as part of the previous job. We would also ignore `build triggers` because this job will be run automatically if our `ahmed-ci-merge` build is stable. (`ahmed-cd` is included in post build actions of `ahmed-ci-merge`)
