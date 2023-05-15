# Tasks
## General info
- Only the contents of your repository's `main` branch that counts
- You will be able to check your code easily with the help of the configured pipeline
- It is advised to use new branches and later on merge them to `main` but it is not mandatory.
## Task 0 - Create your workspace
- Create your own github project. It's name should be your neptun code.
- Invite me as a collaborator to your repo: Settings / Collaborators / Add people (simark2357@gmail.com). Also please send me an email with your repo link.
- Copy the [.gitignore](https://github.com/s1mark/mzl7y1/blob/31674b2071135266cc112cff2f66fa4915e8d871/.gitignore) file to the root of your repository and commit/push your changes to the main branch
- Create your root `main.tf` file
- Enable terraform pipeline in your repository:
  - In the 'Actions' tab search for the 'terraform' keyword and press configure
  - In the generated yaml the 'if' statement in the 'terraform apply' step needs to be changed from `if: github.ref == 'refs/heads/"main"' && github.event_name == 'push'` to `if: github.ref == 'refs/heads/main' && github.event_name == 'push'` otherwise the apply step will not execute in case of pushing to main branch.
  - You can also optionally delete the step that does the 'fmt check'
  - In case of any doubt you can use this [terraform.yml](https://github.com/s1mark/mzl7y1/blob/31674b2071135266cc112cff2f66fa4915e8d871/.github/workflows/terraform.yml) for reference
  - commit your changes to main. At this point you should have the following struture
```
.
├── .github
│   └── workflows
│       └── terraform.yml
│── .gitignore
└── main.tf
```
This repository will be your workspace and you should work on the tasks here.
## Task 1
Create a module named 'files' that:
- should contain 3 variables that are used in the resources
- the `filename` parameter has to start with `${path.module}`
- should generate atleast 1 output
- should be able to create X number of files based on a variable
- create the codebase in the modules/files folder:
```
.
└── modules
    └── files
        │── main.tf
        │── variables.tf
        └── outputs.tf
```
- invoke your module in the root `main.tf` file
- for reference your can check https://github.com/s1mark/mzl7y1
## Task 2
Create a module named 'read' that
- should contain atleast 1 variable
- should generate atleast 1 output
- structure
```
.
└── modules
    └── read
        │── variables.tf
        └── outputs.tf
```
- wire together this module with the 'files' module in a way that it uses atleast one of the outputs from the 'files' module
- the output of the 'read' module should be the input received from the 'files' module with a prefix of "read-"
## Task 3
Create another module named 'write' that
- should contain 5 variables named: `answer_1`, `answer_2`, ..., `answer_5` 
- should output all variables
- read the variables from a file named `answers.tfvars`
```
.
└── modules
    └── write
        │── answers.tfvars
        │── variables.tf
        └── outputs.tf
```
Try to answer to the following questions by using the `answer_x` variables
- Which lifecycle phase is mandatory to interact with resources?
  - state
  - init
  - plan
  - import
- Which is not a valid attribute type?
  - string
  - int
  - tuple
  - object
- Which is an invalid term?
  - for_each
  - count
  - while
  - if
- What is the cleanest way to define dependency between two resources?
  - put them in the same codebase
  - using meta-argument
  - using output values
  - put them in the same module
- Which method of attribute definition has the highest precedence?
  - using -var flag
  - variable's default value
  - exporting  TF_VAR_
  - using .tfvars file 
## Task 4
Create a module named 'data' that
- reads one of the generated files from the 'files' module with the use of the `local_file` datasource
- should dynamically get the path of the generated file as a variable
- should output the `id` of the file
```
.
└── modules
    └── data
        │── main.tf
        │── variables.tf
        └── outputs.tf
```
