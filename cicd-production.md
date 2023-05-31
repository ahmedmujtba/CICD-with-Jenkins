# How to push your code from main to production (ec2)

You need to have an ec2 instance with the app running for this task.

1. Setup another Jenkins project, you can follow the guide [here](./README.md), you'll need to add some aditional configuration as follows:

- In `Source Code Management`, you would need to select `none` for this job, this is because our github branches have already been merged as part of the previous job. We would also ignore `build triggers` because this job will be run automatically if our `ahmed-ci-merge` build is stable. (`ahmed-cd` is included in post build actions of `ahmed-ci-merge`)

- In cd project on jenkins, add the following script to be exceuted in Build:

```
rsync -avz -e "ssh -o StrictHostKeyChecking=no" app ubuntu@ec2-34-249-181-151.eu-west-1.compute.amazonaws.com:/home/ubuntu
ssh -o "StrictHostKeyChecking=no" ubuntu@ec2-34-249-181-151.eu-west-1.compute.amazonaws.com <<EOF
sudo bash ./app/provision.sh
cd app
pm2 kill
pm2 start app.js
EOF
```

NOTE: IP will need to change every time your instance is changed.
