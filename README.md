# Intro to CI/CD Practice Code

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python 3.9](https://img.shields.io/badge/Python-3.9-green.svg)](https://shields.io/)

This repository contains the practice code for the labs in **IBM-CD0215EN-SkillsNetwork Introduction to CI/CD**

## Contents

- Lab 1: [Build an empty Pipeline](labs/01_base_pipeline/README.md)
- Lab 2: [Adding GitHub Triggers](labs/02_add_git_trigger/README.md)
- Lab 3: [Use Tekton CD Catalog](labs/03_use_tekton_catalog/README.md)
- Lab 4: [Integrate Unit Test Automation](labs/04_unit_test_automation/README.md)
- Lab 5: [Building an Image](labs/05_build_an_image/README.md)
- Lab 6: [Deploy to Kubernetes](labs/06_deploy_to_kubernetes/README.md)

## Instructor

John Rofrano, Senior Technical Staff Member, DevOps Champion, @ IBM Research

## Important Commands
* Install git-clone from Tekton Hub: `tkn hub install task git-clone`
* Install flake8 from Tekton Hub: `tkn hub install task flake8`
* Apply the configuration from tasks.yml: `kubectl apply -f tasks.yaml`
* Apply the configuration from pipeline.yml: `kubectl apply -f pipeline.yaml`
* Apply the configuration from pvc.yml: `kubectl apply -f pvc.yaml`  (Persistent Volume Claim)
* Check configured workspace tasks: `tkn task ls`
* Check configures cluster tasks: `tkn clustertask ls`
* Run the pipeline:
  ```tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch=main \
    -p app-name=hitcounter \
    -p build-image=image-registry.openshift-image-registry.svc:5000/$SN_ICR_NAMESPACE/tekton-lab:latest \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    --showlog```
* Check the pipeline status: `tkn pipelinerun ls`
* Check the latest logs: `tkn pipelinerun logs --last`

## <h3 align="center"> © IBM Corporation 2022. All rights reserved. <h3/>
