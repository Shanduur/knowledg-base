# Git Workflows

1. [[#Git Flow]]
2. [[#GitHub Flow]]
3. [[#GitLab Flow]]
4. [[#One Flow]]

## Git Flow

- **Infinite lifetime branches:**
	-   `main` - this branch contains production code. All development code is merged into `main` in sometime.
	-   `develop` - this branch contains pre-production code. When the features are finished then they are merged into develop.
- **Limited lifetime branches:**
	-   `feature-*` - feature branches are used to develop new features for the upcoming releases. May branch off from `develop` and must merge into `develop`.
	-   `hotfix-*` - hotfix branches are necessary to act immediately upon an undesired status of `main`. May branch off from `main` and must merge into `main` and`develop`.
	-   `release-*` - release branches support preparation of a new production release. They allow many minor bug to be fixed and preparation of meta-data for a release. May branch off from `develop` and must merge into `main` and`develop`.

## GitHub Flow

- **Infinite lifetime branches:**
	-   `main` - this branch contains production code. All development code is merged into `main` in sometime.
- **Limited lifetime branches:**
	-   `*` - feature branches are used to develop new features for the upcoming releases. Must branch off from `main` and must merge into `main`.


## GitLab Flow

- **Infinite lifetime branches:**
	-   `main` - this branch contains production code. All development code is merged into `main` in sometime.
	-   `release-*` - release branches support preparation of a new production release. They allow many minor bug to be fixed and preparation of meta-data for a release. Must branch off from `main`.
- **Limited lifetime branches:**
	-   `feature-*` - feature branches are used to develop new features for the upcoming releases. Must branch off from `main` and must merge into `main`.
	-   `hotfix-*` - hotfix branches are necessary to act immediately upon an undesired status of `main`. Must branch off from `main` and must merge into `main`.


### 11 GLF Rules:
1.  Use feature branches, no direct commits on `main`
2.  Test all commits, not only ones on `main`
3.  Run all the tests on all commits (if your tests run longer than 5 minutes have them run in parallel).
4.  Perform code reviews before merges into `main`, not afterwards.
5.  Deployments are automatic, based on branches or tags.
6.  Tags are set by the user, not by CI.
7.  Releases are based on tags.
8.  Pushed commits are never rebased.
9.  Everyone starts from `main`, and targets master.
10.  Fix bugs in `main` first and release branches second.
11.  Commit messages reflect intent.

## One Flow

- **Infinite lifetime branches:**
	-   `release-(n)` - release branches support preparation of a new production release. They allow many minor bug to be fixed and preparation of meta-data for a release. Must branch off from `release-(n-1)` (previous release).
- **Limited lifetime branches:**
	-   `feature-*` - feature branches are used to develop new features for the upcoming releases. Must branch off from `release-(n-1)` and must merge into `release-(n)`.
	-   `hotfix-*` - hotfix branches are necessary to act immediately upon an undesired status of `main`. Must branch off from `release-(n)` and must merge into `release-(n)`.
