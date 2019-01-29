# Pull Request Guidelines

## Background

GitHub pull requests are the critical medium through which the wiki
is created and changed. This forum should be leveraged to improve the quality of content development and invite more open discourse regarding
craftsmanship (style, implementation details, patterns, and best practices).

Without guidelines, pull requests tend to converge on “minimum viability”. A
“minimally viable” pull request contains a code diff and a title because this is
all that is required to create the pull request on Github.

Pull request guidelines are a foundational step towards a better project and content
development practices. Pull request guidelines will nurture a culture of
broader peer review and lower friction across contributors and core team members.

# How to contribute via a Pull Request

> A pull request (PR) is a method of submitting contributions to an open source project. It is often the preferred way of submitting contributions to a project using a Distributed Version Control System (DVCS) such as Git.

FreeCodeCamp is an Open Source project and all of the contents are freely editable.

- [Fork](https://help.github.com/articles/fork-a-repo/) the project on GitHub.
- [Clone](https://help.github.com/articles/cloning-a-repository/) it to a local machine. Do not edit online in github.com, as the editor may cause issues with JSON formatted data.
- [Create a branch](https://help.github.com/articles/creating-and-deleting-branches-within-your-repository/) with the form `fix/some-bug` or `feature/add-cool-thing` and make your changes in that branch and commit them.
- [Push](https://help.github.com/articles/pushing-to-a-remote/) the branch online (if editing locally).
- [Create a pull request](https://help.github.com/articles/creating-a-pull-request/) against the **"staging"** branch.
- The title (also called the subject) of your PR should be descriptive of your changes. i.e. `fixed typo in Hash`
- If the PR is meant to fix a specific issue, append to the end of your PR's commit message `closes #1337`. This tells GitHub to close that issue if the PR is merged.

## Further Reading

- [GitHub & Git Foundations Training](https://www.youtube.com/playlist?list=PLg7s6cbtAD15G8lNyoaYDuKZSKyJrgwB-) - How to use Git and GitHub
- [FreeCodeCamp Contribution Guidelines](https://github.com/FreeCodeCamp/FreeCodeCamp#contributing)
- [How to write Git commit messages](http://chris.beams.io/posts/git-commit/)
- [How to Clone FCC to a Windows PC](FreeCodeCamp-Fork-W

## Guidelines

This section outlines the guidelines that should be imposed upon pull requests for the Ion Wiki.
From this point forward the abbreviation PR will be used in place of “pull request.”

Each PR will:
  1. Include a reference to the Issue it is addressing, if it addresses an issue. This should take the
     following form {subdivision}-{number} tag as the first part of the title where {subdivision} is the
     branch of content and {number} is the Issue number. Example: "CONTENT-11". The ticket
     number should be part of the title not the PR body.
  2. Include a title that provides a one sentence overview of the purpose of the
     PR. Abbreviations can be used when necessary. Example: “PLAT-433 put the
     thumbnail under the original dir in the thumb path”.
  3. Contain a description written using complete sentences of the changes being
     made and any context necessary to understand them.
       1. [optional] An @ message to the stakeholders and reviewers of the PR.
          Example: “/cc @ryan-shea”.
       2. If the PR contains multiple tasks it can be useful to provide them in form of [Task List](https://github.com/blog/1825-task-lists-in-all-markdown-documents). This can also help to track the progress inside the PR and encourage team members to join and help with uncompleted work.
  4. The source code diff. This is provided by Github automatically.
  5. Tests for behavioral changes made to the code.
  6. Be reviewed and approved by someone other than the author.

Finally, PRs should be atomic. That is, they should address one item (task, bug,
story, etc). Exceptions to this requirement may exist (such as content dumps) but they
should be the exception.

## On Merging

Below are some general guidelines on how merging should be handled

First, a PR should not be merged to `master` if any of the following apply:
  * Comments asking for clarification that have not been addressed.
  * An explicit request to not merge.
  * A PR that was explicitly identified as a “work in progress”.

Next, a PR should not be merged unless it has been reviewed by at least one
other person on the team.

## Conclusion

Pull requests are the medium of collaboration and critique within a
Github-based project. It is the primary place where
designs are reviewed, standards are maintained, and where critical discourse
can happen around software craftsmanship and professionalism.

Pull requests play a critical role establishing and maintaining software
craftsmanship within an organization. By establishing guidelines that will
improve the visibility and context of software changes we can encourage better
software craftsmanship through peer review.

## See Also

  * [Github - How to write perfect PR](https://github.com/blog/1943-how-to-write-the-perfect-pull-request)
  * [Tim Pope’s git commit message suggestions](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
  * [MediaWiki commit message guidelines](https://www.mediawiki.org/wiki/Gerrit/Commit_message_guidelines)
  * [MediaWiki code review guidelines](https://www.mediawiki.org/wiki/Gerrit/Code_review)
  * [Thoughtbot code review guidelines](https://github.com/thoughtbot/guides/tree/master/code-review)
