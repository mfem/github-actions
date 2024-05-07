# Welcome to the MFEM GitHub actions repository

The github actions in this repo are used in several projects.

The projects mentioned in [README.md](README.md) are considered critical users of this repo. When introducing a change in this repo, 
care should be taken to check that those will not break the CI process of the critical users.

The verification process is as follow:
- Create a branch with the changes in the GitHub actions repo. Push this branch to the GitHub repo. Give the branch a name that describes the changes, rather than the version number.
- Create branches out of current `master` in the projects mentioned in [README.md](README.md). In those branches, point the GitHub actions to your new branch.
- Create pull requests, marked as `do-not-merge` in the projects so that CI is triggered with your new changes.
- Once working, submit a PR to pull your branch into the `master` branch of the GitHub actions repo.
- Once the commit is merged, tag the merged commit in `master` with a version number: `vX.Y`.
