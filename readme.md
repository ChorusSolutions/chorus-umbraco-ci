# Overview
Chorus' standard CI build (+in future release) YAML template for Umbraco websites.

# Usage
Please read the guidance on using our build templates [here](https://github.com/ChorusSolutions/chorus-yaml-ci).
Note especially the bit on targetting a specific version, not master!

You can see a summary of releases [here](releases.md).

## Creating Your Build
Call the template from your project's yml file like this:

```yaml
queue: Hosted VS2017

resources:
  repositories:
  - repository: umbraco-ci
    type: github
    endpoint: github-endpoint
    name: ChorusSolutions/chorus-umbraco-ci
    ref: refs/tags/{TAG NAME}

steps:

- template: template/umbraco-ci.yml@umbraco-ci
  parameters:
    slnPath: demo/Chorus.UmbracoCI.Demo/Chorus.UmbracoCI.Demo.sln
```

Making sure to set the slnPath appropriately. Replace {TAG NAME} with the tag in this GitHub repo you wish to target.

You can add other steps before/after the template call as needed.
But currently the template will publish artifacts, so we may need to change it as requirements become clear.

## Parameters
These params are optional:

| Parameter | Example | Description |
| --------- | ------- | ----------- |
| slnPath   | /slnFolder/MySln.sln | (Required) The path to the solution. Can use standard VSTS wildcards e.g. **\\*.sln |
| nugetFeedGuid | '7bc11f63-3a1b-488c-8652-322b2858ce02' | (Optional) Guid (or name) of the VSTS NuGet feed to pull from. Defaults to the Chorus feed |
| artifactName | 'Drop' | (Optional) Name of the artifact to create |


# Contributing
This GitHub repo requires PR and working CI build, as for normal Chorus repos in VSTS.

## Demo
A standard .NET project is provided as a demo...this should become an Umbraco project in future to make the demo/testing better.