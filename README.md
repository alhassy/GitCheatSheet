<h1> GitCheatSheet </h1>

Reference of basic commands to get comfortable with Git at the command line, and magit.

**The listing sheet, as PDF, can be found [here](https://github.com/alhassy/GitCheatSheet/blob/master/CheatSheet.pdf)**, while below is a quick-n-dirty html rendition.

This reference sheet is built around the system <https://github.com/alhassy/CheatSheet>

<object width="600" height="400" data="CheatSheet.pdf"></object>

<hr> <hr> <hr>


# Table of Contents

1.  [Workflow \(⟨\)](#orgf9bf4bc)
2.  [Getting started](#org58954dc)
3.  [Branches](#org817e93b)
4.  [Making Changes](#org8c006c5)
5.  [Undoing Changes](#orgbc13ec7)
6.  [Refactoring Filenames](#orgea2656a)
7.  [What changed? &#x2013;Reviewing our history](#orgf7dd248)

<a id="orgf9bf4bc"></a>

# Workflow \(⟨\)

*&#x2013;Getting things done--*

1.  Create a branch, say off of Master.
2.  Work :: Make branches, make commits, push and pull changes, review history.
3.  Merge it back to the parent, e.g., Master, when done.


<a id="org58954dc"></a>

# Getting started

Insist that our Git related actions will be stamped by our identifiying information,
so that it's clear what we did.

    git config --global user.name "⟨My Name⟩"
    git config --global user.email ⟨myEmail@example.com⟩
    
    # Add our GitHub username to our configuration, this is case sensative.
    git config --global user.username ⟨userName⟩
    
    # Open the global configuration file in a text editor for manual editing.
    git config --global --edit


<a id="org817e93b"></a>

# Branches

*&#x2013;Group changes by naming a series of commits and combining completed efforts--*

When contributing, work on a branch: A copy of the original project, with its own history
and its changes are isolated from the original, until it's merged back into the original branch 
&#x2013;which is commonly called “master”.

Do so to avoiding stepping on another contributor's efforts, or having them step on yours,
and also an excellent idea for experimenting: When unsure what's best, experiment on separate branches
then compare your approaches. &#x2013;we can even branch off of any branch!

-   **git branch ⟨branch⟩:** Create a new branch which is a copy of the current branch.
    -   Omitting any name yields the branches available; `git branch -a` shows all branches
        including remote ones. The current branch is marked with an asterisk.

-   **git checkout ⟨branch⟩:** Switch to a given branch.
    -   Create and check out a new branch with `git checkout -b ⟨name⟩`.

-   **git merge:** We apply the changes of the current branch to its parent branch.

-   **git branch -d ⟨branch⟩:** When a branch is no longer needed, and has been merged, we delete it.
-   **git branch -m ⟨newBranchName⟩:** Rename the branch we're currently on.


<a id="org8c006c5"></a>

# Making Changes

*Review edits and craf a commit transaction*

A commit represents the state of our repository at a given point in time.
It's like a snapshot, which we can go back to and see how thing were when we took it.

-   **git add ⟨file⟩:** Snapshots the file in preparation for versioning
-   **git diff:** Shows file differences not yet staged.
-   **git diff &#x2013;staged:** Shows file differences between staging and the last file version
-   **git status:** Show information about the current state of the repository:
    What is the current branch, is everything up to date, what's new, what's changed.
-   **git commit -m "⟨descriptive message⟩":** Records file snapshots permanently in version history
-   **git show ⟨commit⟩:** To see what was new in a commit we can run `git show commit-id-here`.


<a id="orgbc13ec7"></a>

# Undoing Changes

Git allows us to return any selected file back to the way it was in a certain commit.

-   **git checkout ⟨commit⟩ ⟨file⟩:** Reverse everything done to a file to since the given commit.

Erase mistakes and craf replacement history in *local* work.

-   **git reset &#x2013;hard ⟨commit⟩:** Discards all history and changes back to the specified commit
-   **git reset ⟨commit⟩:** Undoes all commits afer ⟨commit⟩, preserving changes locally
-   **git reset ⟨file⟩:** Unstages the file, but preserve its contents

For changes already pushed, we use `git revert` which undoes the changes of a given commit.

-   **git revert HEAD:** The newest commit can be accessed by the `HEAD` alias.
    -   For other commits it's best to use an id; e.g., `git revert b10cc123.`


<a id="orgea2656a"></a>

# Refactoring Filenames

Relocate and remove versioned files

-   **git rm ⟨file⟩:** Deletes the file from the working directory and stages the deletion
-   **git rm &#x2013;cached ⟨file⟩:** Removes the file from version control but preserves the file locally
-   **git mv ⟨file-original⟩ ⟨file-renamed⟩:** Changes the file name and prepares it for commit


<a id="orgf7dd248"></a>

# What changed? &#x2013;Reviewing our history

*Browse and inspect the evolution of project files*

-   **git whatchanged:** Display the entire commit history along with which files were altered in each commit.
-   **git log &#x2013;oneline:** Lists version history for the current branch in one line for each commit.
-   **git log &#x2013;author=“⟨pattern⟩”:** Search for commits by a particular author.
-   **git log -p:** Display the full diff of each commit.
-   **git log &#x2013;grep=“⟨pattern⟩”:** Search for commits with a commit message that matches ⟨pattern⟩.
-   **git log &#x2013; ⟨file⟩:** Only display commits that have the specified file.
