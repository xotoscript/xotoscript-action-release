
## Intro

This pipeline will bump the version in package.json, create a new tag version, update the changelog and push the commit with --follow-tags! This package uses the same pipeline for versioning.

We have the action which contains the release pipeline that will be shared across all our repos :

- action.yml

## Parameters

- release_as : patch, minor, major
- push_to : to support pushing on staging automatically if we want to
- publish_type : to describe what type of publishing type it is : example library vs service,
- pre_action lets you choose actions before starting the script

## Usage Example

you can impliment this custom action in your service by adding :

```yaml
    - name: Release package
        uses: xotoscipt/xotoscript-action-release@v0.0.7
        with:
          release_as: ${{ inputs.release_as }}
```

