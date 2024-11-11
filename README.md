Azure DevOps Static Validation Pipeline:
This pipeline performs static validation tasks including tag checking, generating Terraform documentation, and running Super-Linter to enforce code standards across repositories. Each task is highly customizable, enabling or disabling features as needed through parameters.

Pipeline Stages and Templates:
Scan Stage        : This stage performs the following validation steps:
TagLint           : Checks if version tags exist based on a version.json file and tags code versions accordingly.
TF Docs Generation: Creates or updates README.md documentation using Terraform Docs for easier reference.
Super-Linter      : Runs code linters for Terraform, YAML, Markdown, and more, ensuring code quality and consistency.

Each validation step utilizes templates, with continueOnError settings based on the FailOnFindings parameter to allow flexibility in handling validation outcomes.

YAML Templates Overview:
superlinter.yml: Runs Super-Linter in a Docker container with a configuration for linting various file types.
taglint.yml    : Reads version.json to check and tag code if a matching version does not already exist.
tfdocs.yml     : Runs Terraform Docs to generate a structured README.md file.