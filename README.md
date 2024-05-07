# Welcome to the MFEM GitHub actions repository

The goal of this repository is to gather the GitHub actions used by MFEM, projects related to MFEM, or any other project 
interested in using them. Keeping these in one repo avoids duplicating and maintaining several copies of similar actions.

Projects using these actions:
- [mfem/mfem](https://github.com/mfem/mfem)
- [mfem/pymfem](https://github.com/mfem/pymfem)
- [glvis/glvis](https://github.com/glvis/glvis)
- [ceed/laghos](https://github.com/ceed/laghos)
- [ceed/remhos](https://github.com/ceed/remhos)

Description of the actions:
- [`build-hypre`](build-hypre/action.yml) will download and build hypre with some degree of configuration, dictated by mfem typical usage.
- [`build-metis`](build-metis/action.yml) will download and build metis with some degree of configuration, dictated by mfem typical usage.
- [`build-mfem`](build-mfem/action.yml) will download and build mfem. This one has more configuration options, since we want to enable building various mfem configurations. It is also intended to build mfem both as the main project (in mfem CI) or as a dependency, in which case one can control what repo and branch to use.
- [`upload-coverage`](upload-coverage/action.yml) is a standard action to upload coverage information to codecov.
- [`build-pymfem`](build-pymfem/action.yml) will download and build pymfem, along with its dependencies.
