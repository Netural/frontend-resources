# Git

Largely inspired by [Git Style Guide](https://github.com/agis-/git-style-guide). 


# Table of contents

1. [Branches](#branches)
2. [Commits](#commits)
3. [Misc.](#misc)

## Branches

- We use a slightly modified version of [Gitflow](http://nvie.com/posts/a-successful-git-branching-model/) as a branching model. 

- Choose *short* and *descriptive* names:

    ```shell
    # good
    $ git checkout -b feature/add-contact-forms

    # bad - too vague
    $ git checkout -b feature/language_fix
    ```

- Use *dashes* to separate words. 

- Use a forward slash to categorize your branch:
    
    ```shell
    # good
    $ git checkout -b feature/add-contact-forms
    $ git checkout -b hotfix/2545-stylebook-teaser-links
    $ git checkout -b release/1.3.2 

    # bad - not categorized in git guis (Tower, Sourcetree, ...)
    $ git checkout -b feature-some-changes
    $ git checkout -b hotfix-no-number
    $ git checkout -b release-20171204-somechange
    ```

- Prefix your hotfix branches with the issue number from JIRA or Freshdesk (in case Freshdesk is still used, when you are reading this). 
  For feature branches this is not necessary.

    ```shell
    # JIRA bug #BSP-35
    $ git checkout -b hotfix/35-smaller-headline-size
    ```

- Delete your branch from the upstream repository after it's merged, unless there is a specific reason not to.


## Commits

- Each commit should be a single *logical change*. Don't make several *logical changes* in one commit. 
  For example, if a patch fixes a bug and optimizes the performance of a feature, split it into two separate commits.

  *Tip: Use `git add -p` to interactively stage specific portions of the
  modified files.*

- Don't split a single *logical change* into several commits. For example,
  the implementation of a feature and the corresponding tests should be in the
  same commit.

- Commit *early* and *often*. Small, self-contained commits are easier to
  understand and revert when something goes wrong.

- Commits should be ordered *logically*. For example, if *commit X* depends
  on changes done in *commit Y*, then *commit Y* should come before *commit X*.

Note: While working alone on a local branch that *has not yet been pushed*, it's
fine to use commits as temporary snapshots of your work. However, it still
holds true that you should apply all of the above *before* pushing it.


- The summary line (ie. the first line of the message) should be
  *descriptive* yet *succinct*. Ideally, it should be no longer than
  *50 characters*. It should be capitalized and written in imperative present
  tense. It should not end with a period since it is effectively the commit
  *title*:

  ```shell
  # good - imperative present tense, capitalized, fewer than 50 characters
  Mark huge records as obsolete when clearing hinting faults

  # bad
  fixed ActiveModel::Errors deprecation messages failing when AR was used outside of Rails.
  ```

- After that should come a blank line followed by a more thorough
  description. It should be wrapped to *72 characters* and explain *why*
  the change is needed, *how* it addresses the issue and what *side-effects*
  it might have.

  It should also provide any pointers to related resources (eg. link to the
  corresponding issue in a bug tracker):

  ```text
  Short (50 chars or fewer) summary of changes

  More detailed explanatory text, if necessary. Wrap it to
  72 characters. In some contexts, the first
  line is treated as the subject of an email and the rest of
  the text as the body.  The blank line separating the
  summary from the body is critical (unless you omit the body
  entirely); tools like rebase can get confused if you run
  the two together.

  Further paragraphs come after blank lines.

  - Bullet points are okay, too

  - Use a hyphen or an asterisk for the bullet,
    followed by a single space, with blank lines in
    between

  Source http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
  ```

  Ultimately, when writing a commit message, think about what you would need
  to know if you run across the commit in a year from now.

## Misc.

- There are various workflows and each one has its strengths and weaknesses.
  Whether a workflow fits your case, depends on the team, the project and your
  development procedures.

- *Be consistent.* This is related to the workflow but also expands to things
  like commit messages, branch names and tags. Having a consistent style
  throughout the repository makes it easy to understand what is going on by
  looking at the log, a commit message etc.

- *Test before you push.* Do not push half-done work.


# Inspired by

Agis Anastasopoulos / [@agisanast](https://twitter.com/agisanast) / http://agis.io
... and [contributors](https://github.com/agis-/git-style-guide/graphs/contributors)!
