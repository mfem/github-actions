# Welcome to the MFEM GitHub actions repository

The github actions in this repo are used in several projects.

The projects mentioned in [README.md](README.md) are considered critical users of this repo.
When introducing a change in this repo, care should be taken to check that those changes will not break the CI process of the critical users.

To submit a change please follow the guidelines described below.

## Basics
### Pointing to a specific action
The syntax for using a public action in a subdirectory is as follows ([reference](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#example-using-a-public-action-in-a-subdirectory)):
```
uses: {owner}/{repo}/{path}@{ref}
```

For example:
```
uses: mfem/github-actions/build-hypre@v2.4
```
`{ref}` can be *any* of the following:
- branch
- tag
- commit hash

## Guidelines
To submit a change please follow these guidelines.
Because this involves making changes in multiple repos, each step will be marked with the repo it is referencing:
 - `actions` refers to making a change in this repo: `mfem/github-actions`
 - `project` refers to making a change in the repo with a workflow invoking an action, e.g. one of the projects mentioned in [README.md](README.md)

### Steps
1. `actions` Create a branch from `master` with a descriptive name, e.g. `add-single-precision-ci`
2. `actions` Make updates to actions and push changes
3. `project` Create a new branch and in that branch, change `{ref}` in the workflows you'd like to test so that it points to your feature branch, e.g.
> `mfem/.github/workflows/build-and-tests.yml`
> ```diff
> - uses: mfem/github-actions/build-mfem@v2.4
> + uses: mfem/github-actions/build-mfem@add-single-precision-ci
> ```
4. `project` To test the updated workflow, create a pull request and label it with `DO-NOT-MERGE`; this will trigger the CI to run with your new changes

> **Note**
>
> Adding an option to use manually trigger can be useful for debugging. This can be done by adding `workflow_dispatch` to the list of triggers
> ```
> on:
>   workflow_dispatch
> ```
> The option to manually trigger will not appear until the workflow has previously been triggered via something like a PR or push.

5. `actions` Continue to develop and test your action; because the `{ref}` in your `project` workflow is pointing to your branch, re-running the `project` CI will always point to the latest commit.

6. `actions` Once your changes are finalized, submit a PR to pull your branch into `master`
7. `actions` *Tag* the merged commit with a new [version number](https://semver.org/) `vX.Y`
8. `project` Update the `{ref}` in your actions to point to the new version number, e.g.
> `mfem/.github/workflows/build-and-tests.yml`
> ```diff
> - uses: mfem/github-actions/build-mfem@add-single-precision-ci
> + uses: mfem/github-actions/build-mfem@v2.5
> ```
9. `project` Remove the `DO-NOT-MERGE` label from your PR and complete the merge.
10. Celebrate! 🕺💃🎉

In summary:
Please try to use branches for development and tags for production.

## Tips

- When adding a new input to an action, you may want to also add a new dimension to the job matrix for workflows that use that action. If you are adding a dimension to a job matrix, the job name may also need to be modified as job names must be unique.
