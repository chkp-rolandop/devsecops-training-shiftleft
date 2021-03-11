# devsecops-training-shiftleft

## Set up pipeline with GitHub Actions

- Create github action simple workflow - rename to shiftleft.yml
    - Go to github repository &rightarrow; Actions &rightarrow; Set up Simple Workflow &rightarrow; rename blank.yml to shiftleft.yml
- add credentials into repo secrets
    - https://docs.github.com/en/actions/reference/encrypted-secrets#creating-encrypted-secrets-for-a-repository
- add shiftleft binary into repo
- fork https://github.com/ilavender/demo-app
- set env variable secrets in yaml file
    - https://docs.github.com/en/actions/reference/encrypted-secrets#using-encrypted-secrets-in-a-workflow

## In shiftleft.yaml configure the following:
- clone demo-app 
- run shiftleft source code scan
- build docker image
    - docker build -t chkp-rolandop/myapp ./demo-app
    - docker save -o myapp.tar chkp-rolandop/myapp
- run shiftleft image scan
- run iac-assessment scan on demo-app/terraform-template folder with AWS CIS foundations terraform ruleset

    Note:  Figure out the commands to run locally before adding them to shiftleft.yml


### Check your work agains the shiftleft.yml included in this repo.
