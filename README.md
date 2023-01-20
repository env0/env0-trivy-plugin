<div align="center">
  <img src="https://github.com/aquasecurity/trivy/blob/main/brand/Trivy-OSS-Logo-Color-Horizontal-RGB-2022.svg?raw=true" width="300">
</div>

# env0-trivy-plugin
This env0 trivy Plugin will allow you to run trivy analysis on an IaC directory as a part of your custom flow. To use this plugin, you will need to use version 2 of env0.yml.

## Inputs



The tfsec plugin accepts the following inputs:

* `version` (required) - the specific version of tfsec you wish to use 

* `directory` (required) - the path to the directory with the IaC code to analyze (the root folder is your project's root folder)

* `global-flags` - a string containing global flags as one string, read more [here](https://aquasecurity.github.io/trivy/v0.36/docs/references/customization/config-file/#global-options)

* `flags` - a string containing additional flags as one string, read more [here](https://aquasecurity.github.io/trivy/v0.36/docs/references/cli/config/)


## Example Usage



In this example we will run `tfsec` analysis on your root folder before the "Terraform Plan" step of a deploy. We will call that step "My Step Name":

```yaml
version: 2
deploy:
  steps:
    terraformPlan:
      before:
        - name: My Step Name # The name that will be presented in the UI for this step
          use: https://github.com/env0/env0-trivy-plugin
          inputs:
            version: v0.36.1
            directory: .
            global-flags: --format table
            flags: --exit-code 1

```


## Further Reading

You can read more about `Trivy` and the available flags [here](https://aquasecurity.github.io/trivy).

