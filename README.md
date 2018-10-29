# toy
placeholder for start-git

## Why start-git ??

Using the "start-git" helper script ensures that every repo begins life with its initial commit object as the 'empty' project.
This allows each and every repo to be "pairable" with any other.  That turns out to be a very handy property.
Specifically, it means that all repo's can be easily merged together via regular git operations.
It also allows one to compare pairs of arbitrary project repos in order to detect when there are objects (files) which have identical content - i.e. have been manually copied.  There's always the possiblity of "individual invention", however it's much more likely the file has been 'derived' from another effort.

## Assumptions:

1. local repo names follow a convention of using a suffix indicating their repository hosting service, such as -github or -apache.
2. some repo's have a username- prefix to indicate the initial author, or significant contributor of a fork or branch.
3. collect git repo's (i.e. projects) within a set of directories named 'git-projects'.

    ${HOME}/git-projects - personal activities
    ${HOME}/<org>/git-projects - activites done on behalf of others

## How to begin ?

A project workflow begins via the 'start-git' script.
The project directory (folder) is created by this helper (don't make the directory yourself).
The initial commit is tagged: 'init'.
All of the git repo starts it's existence locally and work can begin in earnest w/o associating the repo with a hosting service.

When the project reaches critical mass, or when there's an actual need to colaborate on the work, a few steps are necessary.  Pick a formal name for the project, establish initial ownership, decide where the source-of-truth will reside (hosting service), and populate it:

    REPO=toys
    OWNER=bjla93334
    SERVICE=github.com

    git remote add origin https://${SERVICE}/${OWNER}/${REPO}.git
    git push origin master

In the case of github one needs to establish the repo's existence on the hosting service before the 'push' can happen.
It's important to be careful to NOT do anything to create content for the project/repo on the hosting service (e.g. "add a README" from the service's browser user interface).

NOTE: The use of 'origin' is magic/arbitrary. This is the default remote-branch name used by 'clone'.  You might want to consider a more complex workflow/release process that involves 'unstable', 'staging', and 'release'.

## Staring feature development:

It's highly advisable to have a 'README' file that covers the basic information about why a project exists.  It's particularly convenient for the content of this document to be in 'markdown' format [ref: Wikipedia, GitHub Flavored Markdown (GFM)].  I recommend you do this first (after start-git) and that you continually check it to ensure that what it says is accurate and complete.  Worse than having no documentation is having documentation that is incomplete, wrong, or otherwise misleading. A few words of advice: take the time to invest in learning GFM plus avoid getting too fancy with your README.md - some folks might not have a formatter handy and resort to reading the raw content.

    git add README.md

## Preliminaries:

From the Wikipedia entry for Git:

"Git is a version-control system for tracking ... files and coordinating work on those files ... it can be used to keep track of changes in any set of files ... support[ing] distributed, non-linear [work].

In a nutshell, git is a power tool.  It is a technology that allows people to manage the information complexity of having to deal with files in a universe that includes many people working concurrently using completely independent filesystems, advancing the content of their files as time marches forward.  Git allows us to deal with the computer equivalent of Einstein's General Relativity - a file-space-time, if you will.

It may very well be that your choice of using Git is intended to be much simpler than this, in which case your intent may be simply to manage your own private, local universe over time like using Apple's Time Machine to capture the history of your work and allow you to refer backward in time to your own earlier work.

However, it's much more likely that you've chosen git because you want to colaborate with others (or you might choose to have multiple personalities - individula feature projects). In which case something you're likely to spend alot of energy on is trying to determine how 2 (or more) different copies of a file compare or contrast with each other.  This is the "difference problem", and understanding this situation can be quite a challenge.

If you're very lucky, when you start to investigate a situation, you may find that the pair of file contents are 'identical'.  Lucky you.  Either you've found that nothing has changed, or perhaps only that someone has moved the file contents around (i.e. file or path renaming).  If you've remembered to use "git mv", you'll be greeting with a "renamed file" indication.  Otherwise, you may find yourself confused by the report of a delete/create file pair.

Most likely you'll find that what has happened is that a simple change to the file's content, in the form of either a simple set of independent "ine additions, line removals, or some of both that are easily recognizable and which make logical sense - don't forget that code review is intended to catch mistakes!

A bit less often you've find that what has happened is that some existing lines (a block) have been moved around, i.e. like renaming some lines have been removed from their old location and added to a new location.

Along with lines moving around, some parts of one or more lines may have been altered.  This could be that parts of a line have been moved around internally, or some text has been added or removed [kinda sensing a general theme here, right?].

What you would really like to have is another power tool - one that's smart enough to sort out all these possiblities and suggest for you what may have happened so that you're able to determine what you believe did happen.  Of course, you could always "call a meeting" of the folks involved in the changes you're investigating. Then you would know for sure what actually did happen.  But, that's not always possible, or practical. [Don't forget to keep notes about your conclusions for later review or reference.]

Now is a really good time to consider your options among available "diff tools".
Selecting one (or more) and learning how they work may prove to be a worthwhile investment that will pay off big in the future.

Here's a contemporary review that I found helpful.  I have a bit of personal baggage, so my preference (first choice) is P4Merge.  Something to keep in mind is that things in this area are continually in flux.  Better options may become available, or the features of a chosen option may change in an undesirable way.  It may be useful to periodically re-survey what's available at any point in time.

    https://www.slant.co/topics/1324/~best-diff-tools-for-git

    https://www.perforce.com/downloads/visual-merge-tool

A possible "helper script" for CLI use:

    exec /Applications/p4merge.app/Contents/Resources/launchp4merge $*:q

## decide upon the project workflow:

