
## Introduction

This pipeline will bump the version in package.json, create a new tag version, update the changelog and push the commit with --follow-tags! This package uses the same pipeline for versioning.

## Parameters

- release_as : for patch, minor, major
- push_to : to support pushing on a specific branch (release, development, etc)
- publish_type : to describe what type of publishing type it is (library vs service, etc)
- pre_action : lets you choose actions before starting the script

## Usage Example

you can implement this custom action in your service by adding :

```yaml
name: ci-release

permissions:
  actions: write
  checks: write
  contents: write
  deployments: write
  id-token: write
  issues: write
  discussions: write
  packages: write
  pages: write
  pull-requests: write
  repository-projects: write
  security-events: write
  statuses: write

on:
  workflow_dispatch:
    inputs:
      release_as:
        description: 'Bump version kind'
        required: true
        default: 'patch'
        type: choice
        options:
        - patch
        - minor
        - major

jobs:
  release:
    runs-on: ubuntu-22.04
    steps:
      - name: release package
        uses: xotoscript/xotoscript-action-release@v0.0.1
        with:
          release_as: ${{ inputs.release_as }}
          push_to: 'staging'
          publish_type: 'library'
```

