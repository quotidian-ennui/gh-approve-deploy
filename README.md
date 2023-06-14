# gh-approve-deploy

This is an extension for [GitHub CLI](https://cli.github.com/) that approves a workflow that has an environment approval gate

I'm using it to approve terraform projects that are gated before `terraform apply` is run.

## Installation

Prerequisites:
 * [GitHub CLI](https://cli.github.com/) is already installed and authenticated
 * [`jq`](https://stedolan.github.io/jq/) is installed

To install this extension:

```
gh extension install quotidian-ennui/gh-approve-deploy
```

## Usage

Assuming that you have an existing workflow that is in a state "waiting" because it needs your approval before continuing... Help is minimal, just inspect the script, it's really not that complicated.

```
cd $DIRECTORY_OF_YOUR_REPO
gh approve-deploy -e 'environment' -w 'workflow-name'
```

```
bsh ❯ gh approve-deploy

Usage: gh approve-deploy -e "environment" -w "workflow-name"
  Required arguments
  -e  The environment requiring approval
  -w  The workflow name

  Optional arguments:
  -b The branch name (default is the default branch)
  -c Comment for the approval (default is 'deploy it')

EXAMPLES
gh approve-deploy -e "production" -w "deploy-to-prod"
```

## License

See [LICENSE](./LICENSE)