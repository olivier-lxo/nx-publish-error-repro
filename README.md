# NxPublishErrorRepro

## Reproduction steps

1. Repository initiated with `npx create-nx-workspace nx-publish-error-repro --preset=ts` (no code formatting, CI provider or remote caching)

2. Added lib with `npx nx g @nx/js:lib packages/mytslib` (and manually fixed node types to v22, maybe could be fixed as well?)

3. Adding release config

4. Bumping version with `npx nx release version`

5. Attempt at publishing package with `npx nx release publish` (doesn't matter if using `--dry-run` or not) fails with error:

```
$ npx nx release publish  --verbose

 NX   Based on your config, the following projects were matched for publishing but do not have the "nx-release-publish" target specified:

- @nx-publish-error-repro/mytslib

This is usually caused by not having an appropriate plugin, such as "@nx/js" installed, which will add the appropriate "nx-release-publish" target for you automatically.

Error: Based on your config, the following projects were matched for publishing but do not have the "nx-release-publish" target specified:
- @nx-publish-error-repro/mytslib

This is usually caused by not having an appropriate plugin, such as "@nx/js" installed, which will add the appropriate "nx-release-publish" target for you automatically.

    at runPublishOnProjects (/tmp/nx-publish-error-repro/node_modules/nx/src/command-line/release/publish.js:153:15)
    at releasePublish (/tmp/nx-publish-error-repro/node_modules/nx/src/command-line/release/publish.js:96:49)
    at processTicksAndRejections (node:internal/process/task_queues:105:5)
    at /tmp/nx-publish-error-repro/node_modules/nx/src/command-line/release/publish.js:21:35
    at handleErrors (/tmp/nx-publish-error-repro/node_modules/nx/src/utils/handle-errors.js:8:24)
    at Object.handler (/tmp/nx-publish-error-repro/node_modules/nx/src/command-line/release/command-object.js:199:24)

```

## Resolve attempts

1. Tried to manually add `@nx/js`

2. Tried multiple release configs
