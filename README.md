# Welcome to the MFEM GitHub actions repository

The goal of this repository is to gather the GitHub actions used by MFEM, projects related to MFEM, or any other project 
interested in using them. Keeping these in one repo avoids duplicating and maintaining several copies of similar actions.

Projects using these actions:
- [mfem/mfem](https://github.com/mfem/mfem)
- [glvis/glvis](https://github.com/glvis/glvis)
- [ceed/laghos](https://github.com/ceed/laghos)
- [ceed/remhos](https://github.com/ceed/remhos)

Description of the actions:
- *build-hypre* will download and build hypre with some degree of configuration, dictated by mfem typical usage.
- *build-metis* will download and build metis with some degree of configuration, dictated by mfem typical usage.
- *build-mfem* will download and build mfem. This one has more configuration options, since we want to enable building various mfem configuration. It is also intended to build mfem both as the main project (in mfem CI) or as a dependency, in which case one can control what repo and branch to use.
- *upload-coverage* is a standard action to upload coverage information to codecov.

