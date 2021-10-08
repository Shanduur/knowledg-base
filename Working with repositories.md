# Working with repositories

1. [Contribution flow](#contribution-flow)
2. [Git branching workflow](#git-branching-flow)
3. [Commit message format](#commit-message-format)
4. [Signing commits](#signing-commits)
5. [Release tags](#release-tags)
6. [New repositories](#new-repositories)

## Contribution flow

1.  Create a topic branch from where you want to base your work (always `main`).
2.  Make commits of logical units.
3.  Make sure your commit messages are in the proper format (see [[#Commit Message Format]])
4.  Push your changes to a topic branch.
5.  Submit a pull request to the `main` branch.
6.  Make sure the tests pass, and add any new tests as appropriate.

## Git branching workflow

We follow a semi-strict convention for branch workflow, commonly known as [GitHub Flow](https://guides.github.com/introduction/flow/). Feature branches are used to develop new features for the upcoming releases. Must branch off from `main` and must merge into `main`. Branch name shall be descriptive. If commits will be referring to the issue, the issue number / tag of the issue shall be included in in the branch name.

```text
fix-123-request-race-prevention
```

## Commit message format

We follow a strict convention for commit messages, known as [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) that is designed to answer two questions: what changed and why. The subject line should feature the what and the body of the commit should describe the why and how.

```text
fix: prevent racing of requests

Introduce a request id and a reference to latest request. Dismiss
incoming responses other than from latest request.

Remove timeouts which were used to mitigate the racing issue but are
obsolete now.

Fixes: #123
```

The format can be described more formally as follows:

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

The first line is the subject and should be no longer than 70 characters, the second line is always blank, and other lines should be wrapped at 80 characters. This allows the message to be easier to read on GitHub as well as in various git tools.

## Signing commits

Every commit that is made, must appear as *Verified*. To achieve this, the GPG signature is used. When committing changes in the local branch, the -S flag must be added to the git commit command:

```bash
$ git commit -S -m your commit message
# Creates a signed commit
```

Alternatively, set up the default key in your `.gitconfig` using the following command:

```bash
$ git config --global user.signingkey [GPG KEY ID]
# sets the [GPG KEY ID] as default signing key
```

To obtain the GPG key, and set it up, refer to the following guides:
- [Signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits)
- [Generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
- [Adding a new GPG key to your GitHub account](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-new-gpg-key-to-your-github-account)
- [Telling Git about your signing key](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)

## Release tags

All releases must be tagged according to [Semantic Versioning 2.0.0](https://semver.org/).

Given a version number `MAJOR.MINOR.PATCH`, increment the:
- `MAJOR` - version when you make incompatible API changes,
- `MINOR` - version when you add functionality in a backward-compatible manner, and
- `PATCH` - version when you make backward-compatible bug fixes.
Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## New repositories

Every new repository should be created from the template repository. The minimal list of files and directories included in the repository:


- `.github` - directory with GitHub specific configurations;
	- `workflows`  - directory containing GitHub Workflows configurations;
		- `signature-check.yml` - signature check pipeline;
- `.commitlintrc.yml` - file containing configuration for the *commitlint*;
- `.drone.yml` - file containing list of pipelines that will be executed on Drone CI;
- `.gitignore` - definition of ignored files and directories;
- `CHANGELOG.md` - all notable changes to the project shall be documented in this file;
- `DCO` - Developer Certificate of Origin;
- `LICENSE.txt` - file containing the license of the software;
- `README.md` - file contining detailed desription of the software;
