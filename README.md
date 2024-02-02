# Custom Vib Image

This template repository is a starting point for creating custom [Vib images](https://github.com/Vanilla-OS/Vib) on top of [official vanilla images](https://images.vanillaos.org) like [desktop image](https://github.com/Vanilla-OS/desktop-image). It contains a basic recipe and an example module to get you started.

It is suggested to checkout the [Vib repository's README](https://github.com/Vanilla-OS/Vib?tab=readme-ov-file#recipe-format) to know more about the recipe format, structure of modules and the supported fields.

## Getting Started

- First, click on the "Use this template" button in top right corner, then from the drop down menu select "Create a new repository". This would create a new repository with the same files and directories as this repository.
- Go to Settings -> Actions -> General and ensure "Allow all actions and reusable workflows" are enabled.
- Now, clone the repository to your local machine and let's start customizing your image. You can also use the github online editor if you prefer.
- Open the `vib-build.yml` workflow file and replace the custom image name with an image name of your choosing in line 11.
- Open the `recipe.yml` file and replace the image name and ID with your image name and ID in line 2 and 3.
- Now, perform your additions and modifications to the recipe as per your requirements.
- Optionally, add your own modules to the `modules` directory and add them in the package-modules includes in `recipe.yml`.

## Explore

Now, that you are aware of the basics, let's explore the files and directories present in this repository:

- `.github/workflows/vib-build.yml`: This file contains the GitHub Actions workflow to check for updates to base image and build the Vib image.
  - It uses the `vib` action to build the recipe and upload it as an artifact. The generated artifact is then built using Docker and pushed to GHCR.
  - The action runs automatically on a schedule checking updates to the base image using [Differ](https://github.com/Vanilla-OS/Differ).
- `.github/workflows/vib-pr.yml`: This file contains the GitHub Actions workflow to build the Vib image on pull requests.
  - It uses the `vib` action to build the recipe and upload it as an artifact. You can download and view the artifact to verify that your changes are performed as expected.
- `.github/dependabot.yml`: This file contains the configuration for GitHub's Dependabot to check for updates to the GitHub actions used in the workflow files monthly and when it finds a new version it creates a PR in your repository.
- `includes.container`: The files included in this directory are added by default to your image to the specified location. (It also contains ABRoot's configuration file)
- `modules`: This directory contains the modules that are used to customize the image. You can add your own modules to this directory.
- `recipe.yml`: This file contains the recipe for the image. It specfies the base image, modules and other fields to be present in the custom image.
