## What does it do?

### Short version.

It gets all configured git repositories and checks out every branch and then checks out the default branch.

### Long version.

Variables used are defined within `getrepos.conf`.

These variables tell `getrepos` all information required to download a list of repositories.

#### Variables used.

name | type | description
---- | ---- | ----
`git_repo` | variable | This is the location of the base git repository.
`git_repo_list` | array | A listing of all repositories to download.
`ext` | variable | The git repository extension.

`getrepos` goes through each repository within `git_repo_list` and performs the following actions in this order:

1. Checks if the repository exists. The following actions are only performed on new repositories.
2. Clones the repository.
3. Gathers information on the default branch.
4. Queries the server for all remote branches.
5. Strips information from the branch names. eg. origin/
6. Checks out each branch to make sure you have local versions. (I do this so IDE's like atom can see the branches correctly.)
7. Checks out the default branch to make sure you are in the branch you would have normally been in after a clone.

## Dependencies

The only dependency `getrepos` has is `rsync`.

It uses rsync to copy the scripts and configs to the correct place.
