# Publishing a new version

1. Update `version` in `package.json` using [SemVer](https://semver.org/)
1. Update `CHANGELOG.md`
1. Run `nvm use` to ensure the correct Node version is used
1. Run `npm install` to update the `package-lock.json`
1. Merge all changes to `main` via a pull request
1. Wait for the CI to pass
1. Create a [new release on GitHub](https://github.com/nationalarchives/tna-frontend/releases/new) and add a new tag in the format `v1.0.0` (ensure leading `v` and change version number as necessary)
1. Add release notes taken from `CHANGELOG.md`

Once a release is created, the [publish pipeline](https://github.com/nationalarchives/tna-frontend/blob/main/.github/workflows/npm-publish.yml) will be triggered.
