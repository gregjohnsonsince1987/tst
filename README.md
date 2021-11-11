# pull-request-based-release-template

Create a release using pull requests.

It was created as a sample repository for the following:

- [slime-hatena/lerna-changelog-action](https://github.com/slime-hatena/lerna-changelog-action)
- [slime-hatena/semantic-versioning-calculator-action](https://github.com/slime-hatena/semantic-versioning-calculator-action)

The license of slime-hatena/pull-request-based-release-template is CC0.  
(If you include the Licence file in this repository, it will also be copied to the repository where you applied the template...)

## About the repository

Automatically do the following:

- Create tags during repository initialization.
- Keep the repository tags.
- Create a branch and Pull Request to be used for the release.
- Create a release with release notes.

This is a git-flow that exclude release branch.

**When merging pull requests, do not use "Squash and merge" and "Rebase and merge". This is a restriction of the lerna-changelog.**

## How to use

1. Create a feature branch, a bug fix branch, etc, from the main branch.  
The changelog will be generated using the title of the pull request. Make only one change per branch.
2. Develop it on the branch.
3. The development is done, create a pull request to the develop branch.
4. When the Pull Request is merged, the `main...develop` Pull Request will be updated.
5. Check the version and release notes to make sure they are correct in the `main...develop` Pull Request.
6. Merge it when you are ready to release.
7. Check the release was created correctly.
8. Make sure that develop branch has been created for the next time.

\* Create a hotfix branch if you need to release before the develop branch. Treat it as you would a develop branch. (Create a new branch. When fix is done, merge it into hotfix branch, set the `Release` tag, and merge it into main branch.)

## Todo

The following tasks are useful to understand easily.

- [ ] Modify README.md to match the contents of the repository.
- [ ] Create a LICENSE.
- [ ] If your build require additional steps, you have to write steps into `.github/workflows/create_release.yml`.
- [ ] To customize the label, edit `.github/labels.json`. To apply the changes, run the `Label maintenance Action` manually.
- [ ] Create a `dependabot.yml` if necessary. You may want to add the following settings: labels: 'Type: Maintenance', target-branch: "develop".
- [ ] The following settings can be added to ensure safe operation.
  - [ ] Setting -> Option -> Allow merge commits. / true.
  - [ ] Setting -> Option -> Allow squash merging. / false.
  - [ ] Setting -> Option -> Allow rebase merging. / false.
  - [ ] Setting -> Option -> Automatically delete head branches. / true.
  - [ ] Setting -> Branch protection rules. / Setup into main.
    - [ ] Require status checks to pass before merging.
    - [ ] Require branches to be up to date before merging.
    - [ ] Require conversation resolution before merging.
    - [ ] Include administrators.
