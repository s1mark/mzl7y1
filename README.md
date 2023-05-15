# Tasks
## Create your workspace
* Create your own github project. It's name should be your neptun code
* Invite me as a collaborator to your repo: Settings / Collaborators / Add people (simark2357@gmail.com). Also please send me an email with your repo link.
* Copy the [.gitignore](https://github.com/s1mark/mzl7y1/blob/31674b2071135266cc112cff2f66fa4915e8d871/.gitignore) file to the root of your repository and commit/push your changes to the main branch
* Enable terraform pipeline in your repository:
** In the 'Actions' tab search for the 'terraform' keyword and press configure
** In the generated yaml file optionally you can delete the step that does the 'fmt check'
** commit your changes to main
At this point you should have the following struture
.
├── .github/
│   └── workflows/
│       └── terraform.yml
└── .gitignore
