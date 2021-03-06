# circleci-support

Images and scripts for testing with CircleCI.

## circleci-python:2.6 image

This container image is derived from
[circleci/python](https://hub.docker.com/r/circleci/python/) images
with the following changes:

- Python 2.6 is installed
- Other Python versions are uninstalled

Image is available at: `quay.io/rohanpm/circleci-python:2.6`

## rohanpm/python orb

An orb is provided for test & release of Python-based projects.

See [rohanpm/python](https://circleci.com/orbs/registry/orb/rohanpm/python)
in the orb registry for usage information.
