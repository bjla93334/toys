# toy
placeholder for start-git

## Why start-git ??

Using the "start-git" helper script ensures that every repo has it's initial commit object be the 'empty' project.
This allows each and every repo to be "pairable" with any other, which turns out to be a very handy property.
Specifically, it means that all repo's can be easily merged together via regular git operations.
It also allows one to compare sets in order to detect when there are objects (files) which have identical content.

## Assumptions:

1. local repo names follow a convention of using a suffix indicating their repository hosting service, such as -github or -apache.
2. some repo's have a username- prefix to indicate the initial author, or significant contributor of a fork.
3. collect git repo's (i.e. projects) within a set of directories named 'git-projects'.

    ${HOME}/git-projects - personal activities
    ${HOME}/<org>/git-projects - activites done on behalf of others

## How to begin ?

Project workflows starts with the 'start-git' script.
The repo/project directory is created by this helper (don't make the directory yourself).
The initial commit is tagged: 'init'.
All of the git repo starts it's existence locally and work can begin in earnest w/o associating the repo with a hosting service.
When the project reaches critical mass, or when there's an actual need to colaborate on the work, 2 steps are necessary:

    git remote add origin https://github.com/bjla93334/${REPO}.git
    git push origin master

In the case of github (at least) one needs to establish the repo's existence on the hosting service before the 'push' can happen.
It's important to be careful to NOT do anything to create content for the repo on the hosting service (e.g. "add a README").

