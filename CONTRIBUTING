The github actions in this repo are used in several projects.

The projects mentioned in the README are considered critical users of this repo. When introducing a change in this repo, care should be taken to check that those will not break the CI process of the critical users.

The verification process is as follow:
- Create a branch with the changes in the github actions. Push this branch to the Github repo.
- Create branches out of current master in the projects mentioned in the README. In those branches, point the github actions to your new branch.
- Create pull requests, marked as "do-not-merge" in the projects so that CI is triggered with your new changes.
- Once working, submit a PR to the github actions repo.
