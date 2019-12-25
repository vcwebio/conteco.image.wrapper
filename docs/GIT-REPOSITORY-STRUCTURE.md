[`image.wrapper`](../README.md) >> GIT Repository Structure

-----

# GIT Repository Structure

The __git__ repository contains the following items:

* `conteco` folder with potentially all the subfolders described in the Common Folder Structure except for `pwd` and `repo`.

* `docs` folder for additional documentation files additional to `README.md` in the repository root.

* `README.md` file as documentation entry point.

* `LICENSE`, the MIT License covering the ContEco orchestrator.

* `Dockerfile`, templated and parameterised build file for the container image. This is the build file used by the ConteEco tools.

* `environment`, the image specific settings used in the building and running of the image.

* `Dockerfile.static`, a static version created by `conteco config build` used by Docker Hub to auto-build the image on GitHub repository update.

-----
[`image.wrapper`](../README.md) >> GIT Repository Structure
