# GitHub Actions for MkDocs and GitHub Pages

Build markdown documentation with [Material for MkDocs] and push to GitHub Pages with GitHub Actions.

[Material for MkDocs]: https://github.com/squidfunk/mkdocs-material

![material.png](https://raw.githubusercontent.com/peaceiris/mkdocs-material-boilerplate/master/docs/images/material.png)



## Sample repository

[peaceiris/mkdocs-material-boilerplate: MkDocs Material Boilerplate (Starter Kit)]

>  Deploy documentation to hosting platforms (Netlify, GitHub Pages, GitLab Pages, and AWS Amplify Console) with CircleCI, Docker, pipenv, GitHub Actions

[peaceiris/mkdocs-material-boilerplate: MkDocs Material Boilerplate (Starter Kit)]: https://github.com/peaceiris/mkdocs-material-boilerplate



## Getting started

### (1) Add deploy Key

1. Generate deploy key `ssh-keygen -t rsa -f mkdocs -q -N ""`
2. Go to "Settings > Deploy Keys" of repository.
3. Add your public key within "Allow write access" option.
4. Go to "Settings > Secrets" of repository.
5. Add your private deploy key as `ACTIONS_DEPLOY_KEY`

### (2) Workflow

```sh
workflow "MkDocs workflow" {
  on = "push"
  resolves = ["Build and deploy"]
}

action "master" {
  uses = "actions/bin/filter@master"
  args = "branch master"
}

action "Build and deploy" {
  needs = "master"
  uses = "peaceiris/actions-mkdocs-gh-pages@master"
  secrets = [
    "ACTIONS_DEPLOY_KEY"
  ]
}
```

### (3) Push to master branch

When you push to master branch, GitHub Actions runs.



## License

[MIT License - peaceiris/actions-mkdocs-gh-pages]

[MIT License - peaceiris/actions-mkdocs-gh-pages]: https://github.com/peaceiris/actions-mkdocs-gh-pages/blob/master/LICENSE
