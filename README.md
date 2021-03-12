# devsecops-training-shiftleft

# WARNING: THIS REPO CONTAINS MALICIOUS FILES

## DevSecOps Lab 1: Create new Repo with name shiftleft-cicd-demo
- Set up Git on CLI
    - git config --global user.name First Last
    - git config --global user.email email-address
- Set up SSH keys for Github
    - [GitHub SSH Key Documentation](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Create new folder
    - mkdir shiftleft-cicd-demo
    - cd shiftleft-cicd-demo
- Create new repository in github.com with name shiftleft-cicd-demo
    - Select Public
    - Leave all checkboxes blank
    - Follow instructions to create repository on the command line

        echo "# shiftleft-cicd-demo" >> README.md\
        git init\
        git add README.md\
        git commit -m "first commit"\
        git branch -M main\
        git remote add origin git@github.com:chkp-rolandop/testlab.git\
        git push -u origin main

## DevSecOps Lab 2: Set up pipeline with GitHub Actions

- Create github action simple workflow - rename to shiftleft.yml
    - Go to github repository &rightarrow; Actions &rightarrow; Set up Simple Workflow &rightarrow; rename blank.yml to shiftleft.yml
- Review yaml syntax
    - [GitHub Actions Syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)
- add credentials into repo secrets
    - [GitHub Actions Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets#creating-encrypted-secrets-for-a-repository)
    - add shiftleft binary into repo
- fork https://github.com/ilavender/demo-app
- set env variable secrets in yaml file
    - [Using Encrypted Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets#using-encrypted-secrets-in-a-workflow) 

## ShiftLeft Lab 1: Clone this repo and run code-scan and image scan
- Clone this repo:  git clone https://github.com/chkp-rolandop/devsecops-training-shiftleft
- Make shiftleft binary executable
    - chmod +x ./shiftleft
- Set up cloudguard credentials
    - export CHKP_CLOUDGUARD_ID=<cloudguard_api_key_id>
    - export CHKP_CLOUDGUARD_SECRET=<cloudguard_api_secret>
- Run code scan
    - ./shiftleft code-scan -s ./test-files
- Build docker image
    - docker build -t chkp-username/myapp ./test-files/Dockerfile
    - docker save -o myapp.tar chkp-username/myapp
    - ./shiftleft image-scan -i myapp.tar

## ShiftLeft Lab 2: In shiftleft.yaml configure the following:
- clone demo-app 
- run shiftleft source code scan
- build docker image
    - docker build -t chkp-rolandop/myapp ./demo-app
    - docker save -o myapp.tar chkp-rolandop/myapp
- run shiftleft image scan
- run iac-assessment scan on demo-app/terraform-template folder with AWS CIS foundations terraform ruleset

    Note:  Figure out the commands to run locally before adding them to shiftleft.yml

### Check your work against the shiftleft.yml included in this repo.
