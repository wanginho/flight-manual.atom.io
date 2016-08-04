---
title: "Publishing"
---

### Publishing

Atom bundles a command line utility called `apm` which we first used back in [Command Line](/using-atom/sections/atom-packages/#command-line) to search for and install packages via the command line. The `apm` command can also be used to publish Atom packages to the public registry and update them.

#### Prepare Your Package

There are a few things you should double check before publishing:

* Your `package.json` file has `name`, `description`, and `repository` fields.
* Your `package.json` file has a `version` field with a value of  `"0.0.0"`.
* Your `package.json` file has an `engines` field that contains an entry for Atom such as: `"engines": {"atom": ">=1.0.0 <2.0.0"}`.
* Your package has a `README.md` file at the root.
* Change the `repository` url in the `package.json` file to match the URL of your repository.
* Your package is in a Git repository that has been pushed to [GitHub](https://github.com). Follow [this guide](http://guides.github.com/overviews/desktop) if your package isn't already on GitHub.

#### Publish Your Package

Before you publish a package it is a good idea to check ahead of time if a package with the same name has already been published to [the atom.io package registry](https://atom.io/packages). You can do that by visiting `https://atom.io/packages/your-package-name` to see if the package already exists. If it does, update your package's name to something that is available before proceeding.

Now let's review what the `apm publish` command does:

1. Registers the package name on atom.io if it is being published for the first time.
2. Updates the `version` field in the `package.json` file and commits it.
3. Creates a new [Git tag](http://git-scm.com/book/en/Git-Basics-Tagging) for the version being published.
4. Pushes the tag and current branch up to GitHub.
5. Updates atom.io with the new version being published.

Now run the following commands to publish your package:

``` command-line
$ cd ~/github/my-package
$ apm publish minor
```

If this is the first package you are publishing, the `apm publish` command may prompt you for your GitHub username and password. This is required to publish and you only need to enter this information the first time you publish. The credentials are stored securely in your [keychain](https://en.wikipedia.org/wiki/Keychain_(Apple)) once you login.

Your package is now published and available on atom.io. Head on over to `https://atom.io/packages/your-package-name` to see your package's page.

With `apm publish`, you can bump the version and publish by using

``` command-line
$ apm publish <version-type>
```

where `<version-type>` can be `major`, `minor` and `patch`.

The `major` option to the publish command tells apm to increment the first number of the version before publishing so the published version will be `1.0.0` and the Git tag created will be `v1.0.0`.

The `minor` option to the publish command tells apm to increment the second number of the version before publishing so the published version will be `0.1.0` and the Git tag created will be `v0.1.0`.

The `patch` option to the publish command tells apm to increment the third number of the version before publishing so the published version will be `0.0.1` and the Git tag created will be `v0.0.1`.

Use `major` when you make a change that breaks backwards compatibility, like changing defaults or removing features. Use `minor` when adding new functionality or making improvements on existing code. Use `patch` when you fix a bug that was causing incorrect behaviour. Check out [semantic versioning](http://semver.org) to learn more about best practices for versioning your package releases.

You can also run `apm help publish` to see all the available options and `apm help` to see all the other available commands.