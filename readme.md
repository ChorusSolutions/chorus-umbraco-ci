# Overview
Chorus' standard CI build (+in future release) YAML templates.

# Usage
TODO: fill this in properly.
Create a standard .yaml build, then use the appropriate template as follows:

???

## Versioning
It's bad practice to reference the current master in your projects, as updates will immediately change your project's CI (without your knowledge).

Instead, reference a specific tag

## Provided Templates
???

# Contributing
## Demo
A standard Umbraco website is provided so that the build can be tested.

## Releasing
The YAML builds in VSTS don't document support for using packages, which may well be our preferred.
For now (until available/POC'd), projects reference from the git repo.

As such, when releasing, make sure a tag is taken on master such that your specific, supported version can be referenced.

Also, be aware that if you change the folder structure/name to the template entry point in the repo, you WILL break everyone's CI when they update!