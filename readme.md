# Overview
Chorus' standard CI build (+in future release) YAML templates.

# Usage
Create a yaml build in your VSTS repo, then reference and call the template in this repo, passing in params as appropriate.

It's recommended that you target the template from a specific tag, so that you're not automatically updated to the latest (potentially breaking) changes.

You can see a summary of releases [here](releases.md).

## Creating Your Build
Create a standard yaml build in your VSTS repo, by having a .vsts-ci.yml file at the root then populate like this:

```yaml
queue: Hosted VS2017

resources:
  repositories:
  - repository: umbraco-ci
    type: github
    endpoint: github-endpoint
    name: ChorusSolutions/chorus-umbraco-ci
    ref: refs/tags/<TAG NAME>

steps:

- template: template/umbraco-ci.yml@umbraco-ci
  parameters:
    slnPath: demo/Chorus.UmbracoCI.Demo/Chorus.UmbracoCI.Demo.sln
```

Making sure to set the slnPath appropriately. Replace <TAG NAME> with the tag in this GitHub repo you wish to target.

You can add other steps before/after the template call as needed.
But currently the template will publish artifacts, so we may need to change it as requirements become clear.

## Advanced Parameters
These params are optional:

| Parameter | Example | Description |
| --------- | ------- | ----------- |
| nugetFeedGuid | '7bc11f63-3a1b-488c-8652-322b2858ce02' | Guid (or name) of the VSTS NuGet feed to pull from. Defaults to the Chorus feed |
| artifactName | 'Drop' | Name of the artifact to create |


# Why's this on GitHub?
Currently, the only way of having external templates for VSTS yaml builds is to pull them from another git repo (no packages support, annoyingly).
However, this feature only supports (at time of writing) pulling from a VSTS repo in the same project! As we have many projects, that doesn't work for Chorus, so we're hosting these on github.

# Contributing
This GitHub repo requires PR and working CI build, as for normal Chorus repos in VSTS.

## Versioning
Please ensure that if you have a new version ready for use it is tagged with a semver release number, as all dependant projects will depend on this to target a specific version (making updates opt in)

## Demo
A standard .NET project is provided as a demo...this should become an Umbraco project in future to make the demo/testing better.