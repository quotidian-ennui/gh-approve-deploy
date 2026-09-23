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

```console
cd $DIRECTORY_OF_YOUR_REPO
gh approve-deploy -w 'workflow-name'
```

```console
bsh ❯ gh approve-deploy

Usage: gh approve-deploy -w "workflow-name"
       gh approve-deploy https://github.com/OWNER/REPO/actions/runs/RUN_ID

  Required arguments (unless a run URL is given)
  -w  The workflow name

  Optional arguments:
  -b The branch name (default is the default branch)
  -c Comment for the approval (default is 'deploy it')
  -l list workflow runs in a 'waiting' state on the branch

  A workflow run URL can be given as a positional argument instead of -w.
  The repository and run id are extracted from the URL, so it works
  outside of a git checkout.

EXAMPLES
gh approve-deploy -w "deploy-to-prod"
gh approve-deploy https://github.com/quotidian-ennui/local-cluster-terraform/actions/runs/35607976874
```

## License

See [LICENSE](./LICENSE)
