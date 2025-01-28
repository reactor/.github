# Contributing to Reactor

:+1::tada: First off, thanks for taking the time to contribute! :tada::+1:

This document gives you guidelines and pointers at how you should approach contributing.

> :warning: ***About links in this document***
> <br>While this document applies to Reactor projects in general, most GitHub links here point to the `reactor-core` repository.
> <br>Make sure to adapt according to the project you are actually targetting (`reactor-netty`, `reactor-addons`, ...).


## :runner: Super Short Version

1. Work from a feature branch
 - Evaluate or ask the team whether the fix should be done in oldest maintenance branch (if there are any active, eg. `3.3.x`)
2. All contributions go through a [Pull Request](#mortar_board-learning-more-about-the-tools-we-use) and code review process, including our own!
3. Make sure to sign your commits using a [Signed-off-by trailer](#clipboard-developer-certificate-of-origin)
4. Include tests
5. Update [license headers](#license-headers) if necessary
6. Make sure commits are focused on a single issue, ideally within a dedicated PR
 - Before merging, we'll strive to have single-concern commit(s) with a [well crafted message](#black_nib-commit-message-convention)
7. Make sure to follow [code style](#art-code-style) and to only reformat changed lines


For more details:
 - [Do you have a question?](#question-do-you-have-a-question)
 - [Deprecation policy](#recycle-our-policy-on-deprecations)
 - [Did you find a bug?](#beetle-did-you-find-a-bug)
 - [Did you write a patch that fixes a bug?](#wrench-did-you-write-a-patch-that-fixes-a-bug)
 - [Do you intend to add a new feature or change an existing one?](#mag-do-you-intend-to-add-a-new-feature-or-change-an-existing-one)
 - [Contributor License Agreement](#clipboard-contributor-license-agreement)
 - [Code style](#art-code-style)
 - [PR and commit style](#sparkles-pr-and-commit-style)
 - > be sure to at least look at the [Commit Message Convention](#black_nib-commit-message-convention)
 - [More details](#speech_balloon-more-details)
 - [Learning more about the tools we use](#mortar_board-learning-more-about-the-tools-we-use)

The Reactor team appreciates your contributing effort! :heart: :heart: :heart:



## :question: Do you have a question?

### Stack Overflow

**Stack Overflow** is the preferred avenue of asking well-researched and focused questions which can later help other users.

We generally discourage opening GitHub issues for questions.

Use relevant tags among the ones we monitor for that purpose:
 - [`reactor-netty`](https://stackoverflow.com/questions/tagged/reactor-netty) for specific reactor-netty questions
 - [`project-reactor`](https://stackoverflow.com/questions/tagged/project-reactor) for generic reactor questions

### Chatting with the community

The Reactor community also gathers on **Gitter** for more freeform discussions.
The team takes more of a backseat in these channels.

We recommend asking the community for help on Gitter in the following cases:

 - you're unsure why something isn't working or wondering if there is a better
way of doing it
 - you have a simple beginner question and prefer getting an answer live
 - you want to chat with other users in the community
 - you need help investigating a particular problem down to the root cause before opening an issue or a Stack Overflow question

The Reactor community Gitter channels are:
 - [`reactor`](https://gitter.im/reactor/reactor): the historic most active one, where most of the community can help
 - [`reactor-netty`](https://gitter.im/reactor/reactor-netty): intended for netty-specific questions

Getting input from the community can sometimes lead to a more focused understanding of the problem, which can turn into either a bug report or a well-researched StackOverflow question :+1:

Please also refer to each project's README for potential other sources of information.

## :recycle: Our policy on **deprecations**

When dealing with deprecations, given a version `A.B.C`, we'll ensure that:

 - deprecations introduced in version `A`.`B`.`0` will be removed **no sooner than** version `A`.**`B+1`**.`0`
 - deprecations introduced in version `A`.`B`.`1+` will be removed **no sooner than** version `A`.**`B+2`**.`0`
 - we'll strive to mention the following in the deprecation javadoc:
   - target minimum version for removal
   - pointers to replacements for the deprecated method
   - version in which method was deprecated

> This policy is officially in effect as of January 2021.

Note that deprecation removal targets are not a hard commitment, and the deprecated methods **could live on further than these minimum target GA versions** (ie. only the most problematic deprecated methods will be removed aggressively).

:warning: That said, deprecated code that has outlived its minimum removal target version may be removed in any subsequent release (including patch releases, aka service releases) without further notice. So users should still strive to update their code as early as possible.

## :beetle: Did you find a bug?

 - **Do not open a GitHub issue if the bug is a security vulnerability in Reactor** (see [SECURITY.md](https://github.com/reactor/.github/blob/main/SECURITY.md))
 - **Ensure the bug was not already reported**: Do a bit of searching
the relevant project's **Issues** (eg. [reactor-core Issues](https://github.com/reactor/reactor-core/issues/)) to see if you
can find something similar
 - If you don't find something similar, **open a new issue** (eg. [reactor-core new issue](https://github.com/reactor/reactor-core/issues/new)).
 Be sure to follow the template and to include a title and clear description.
 Add as much relevant information as possible, and a code sample or an executable test case demonstrating the expected behavior that is not occurring

## :wrench: Did you write a patch that fixes a bug?

 - We no longer require an issue to be opened before a PR. That said, opening an issue first can help in triaging and avoiding wasted effort. For instance, you might need to [target an older branch](#starting-from-the-right-branch)
 - Be sure to sign your commits using a [Signed-off-by trailer](#clipboard-developer-certificate-of-origin)
 - Try to create a branch with a **meaningful name** (see hints [here](#creating-a-branch-with-representative-name))
 - Work on your change. Be sure to include **JUnit test cases**, this will greatly help maintainers while reviewing your change
 - **Run all tests locally** prior to submission: `./gradlew check`
 - Finally, you're **ready to submit** your Pull-Request :+1:

## :mag: Do you intend to add a new feature or change an existing one?
 - Again, **search for similar suggestions** in existing issues (including closed ones)
 - If nothing like that has been suggested before, **discuss it in a new issue first**
 - If you gather positive feedback, **work on the change** following the guideline [above](#wrench-did-you-write-a-patch-that-fixes-a-bug)

### :clipboard: Developer Certificate of Origin

All commits must include a __Signed-off-by__ trailer at the end of each commit message to indicate that the contributor agrees to the Developer Certificate of Origin.
For additional details, please refer to the blog post https://spring.io/blog/2025/01/06/hello-dco-goodbye-cla-simplifying-contributions-to-spring[Hello DCO, Goodbye CLA: Simplifying Contributions to Spring].

## :art: Code style
Please carefully follow the whitespace and formatting conventions already present in the codebase.
Avoid reformatting whole files in favour of changed lines only.

Here is a short summary of the style:

1. Tabs, not spaces
1. Unix (LF), not DOS (CRLF) line endings
1. Eliminate all trailing whitespace
1. Wrap Javadoc at 120 characters
1. Aim to wrap code at 120 characters, but favor readability over wrapping
1. Preserve existing formatting; i.e. do not reformat code for its own sake
1. Open brackets on same line, close brackets isolated on a dedicated new line
1. `else`, `catch`, `finally` on a new line

Each project might have some formatter configuration exported, see [Importing and following the Reactor Code Style](#importing-and-following-the-reactor-code-style) for more details.

## :sparkles: PR and commit style

 - **Commit early and commit often**. Try to still have **descriptive commit messages** though. This helps during the review process, to see through which steps and train of thought you went
 - Once submitted, the review and discussion starts. If necessary, make adjustments in **further commits**
 - Use your **real name** in commits (see [configuration hints](#using-real-names))
 - _Once the PR is **approved**_ :white_check_mark: , clean up and **prepare for merge** (see [From PR to main](#from-pr-to-main))

### :black_nib: Commit Message Convention
We use the following convention for commit message title and body:

```
[{OPTIONAL_TAG}] {TITLE} (#{PR})

Longer description of the content of the commit and/or context of the
changed, hard-wrapped at 72 characters

See #{OPTIONAL_REF}.
Fixes #{ISSUE}.
```

 - `{TITLE}` should be a **short but meaningful description** of the fix, preferably under 50 chars (the whole line, including tag and pr link, should NOT go over 72 chars)
 - `{PR}` is the PR identifier, which will be appended at the end of the review process most of the time
  - this ensures we can find PRs and discussions when starting from a commit
  - if your PR contains several commits (which should generally [be avoided](#from-pr-to-main)), reword the commits so that they all include this `#{PR}` link
 - Additionally we sometimes use `[{OPTIONAL_TAG}]` like `[polish]`, `[test]`, `[doc]` or `[build]` followed by one space
 - The description body should focus on the **Why** of the change, not the How
 - At the end of the description body, you can include references:
  - ids of related issues or PRs in `See #{OPTIONAL_REF}.` format
  - **the id of the issue that is fixed by this PR (if any) in `Fixes #{ISSUE}.` format** (so that it will get closed once the PR is merged)

See [More about commits](#message-convention) for a more detailed example.

## :speech_balloon: More details

### Starting from the right branch

Issues are useful before opening a pull-request because they allow the Reactor
team to do some triage, answer questions and help with designing a fix.

Additionally, during the triage process the team will evaluate the criticality
of the reported issue and decide wether or not it should also be fixed in current
maintenance branche(s).

If this is the case, the fix should be implemented against the earliest relevant
maintenance branch, which will be indicated in the issue as the _milestone_.

For instance, if an issue should be fixed in both 3.3 and 3.4, the later being
developed on main, the fix PR should be opened against `3.3.x` (and the issue
will be triaged into `3.3.x Backlog`).

If on the other hand the issue should only be fixed in the next feature release,
assuming `3.4.x` is the current main line it will be affected to the `3.4.x Backlog`
triage milestone and should be developed against `main`.

### From PR to `main`
For each PR, there will generally be **a single commit** that goes into `main` (or formerly `master`). We will try to use the `squash-and-merge` strategy on GitHub to that effect.

Another case where your help is needed in preparing for merge is **if your PR has a few logical changes**, and you'd like to have as many commits.
(Note that if you have more than, say, 3 of these, it's probably that you actually need to do several PRs).
If you want us to rebase-and-merge, you'll need to let us know and to perform a manual `git rebase -i BASE_BRANCH` in order to prepare the commits.
You'll probably need to at least squash intermediate commits from the "commit early and often" side of things, and to ensure that the final commits all follow the message convention.

If you're targetting the maintenance branch, see the following discussion:
https://github.com/reactor/reactor-core/issues/1225

TL;DR: as a maintainer, use `git merge --no-ff --no-commit 3.3.x` and `Merge #xxxx into 3.4.123` (where `3.3.x` is the maintenance branch and `3.4.123` is the upcoming release of the latest generation). Once done, add 👍 or 🚀 on the bot's message.

We tend to put the oldest maintenance branch as the milestone of the issue and the newest milestone in which it was forward merged as the milestone of the pr (when there is both an issue and PR).
If there is only a PR, use the oldest milestone in which it will be released.


### Creating a branch with representative name

If there is a corresponding open issue, the branch used when submitting a pull request
should preferably be named according to the `xxx-shortDescription` convention:

 - `xxx` is the github issue number if any
 - use a `-` separator, at least after issue number
 - `shortDescription` should be a few representative words about the issue
 
For example: `1226-lastOnEmptyCallable`.


### More about commits

#### Message convention
Here is a more detailed example of the commit message convention,
applied to PR 1235 (which fixes issue 1234 and is related to an
older discussion which happened in issue 1000):

```
Prefer short (50 chars) summary of changes (#1235)

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body. The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Further paragraphs come after blank lines.

 - Bullet points are okay, too
 - Typically a hyphen or asterisk is used for the bullet, preceded by a
   single space, but conventions vary here

Below we demonstrate linking to an older related issue, as well as
closing the issue fixed by this pull-request. One can also use the
`gh-1234` format instead of `#1234` for such references. Then one
paragraph further down is an example of optional git trailers.

See #1000 for some reason explained briefly here.
Fixes #1234.

Signed-off-by: John Doe <jonh@example.com>
Co-authored-by: Jane Doe <jane@example.com>
```


1. Use imperative statements in the subject line, e.g. "Fix broken Javadoc link".
1. Begin the DESCRIPTION with a capitalized verb, e.g. "Add, Prune, Fix,
    Introduce, Avoid, etc."
1. Do not end the subject line with a period.
1. Restrict the subject line to 72 characters or less (accommodating for PR reference)
1. Wrap lines in the body at 72 characters or less.
1. In the body of the commit message, explain the context of the change, and why
things were changed the way they were. The How is in the code.
1. If the commit is fixing issue XXX, make sure to include `Fixes #XXXX.` at the end
of the body (but before any git trailers)
1. Git defines the notion of "trailers", like `Signed-off-by:` or `Co-authored-by:`.
These must always go at the very end.

#### Using real names
Please configure git to use your real first and last name for any commits you
intend to submit as pull requests. For example, this is not acceptable:

    Author: Nickname <user@mail.com>

Rather, please include your first and last name, properly capitalized.

    Author: First Last <user@mail.com>

You can configure this via the account admin area in GitHub (useful for
fork-and-edit cases); _globally_ on your machine with

    git config --global user.name "First Last"
    git config --global user.email user@mail.com

or _locally_ for the `reactor-core` repository only by omitting the
'--global' flag:

    cd reactor-core
    git config user.name "First Last"
    git config user.email user@mail.com
    
### Importing and following the Reactor Code Style

Please carefully follow the whitespace and formatting conventions already present in the codebase.
Avoid reformatting whole files in favour of changed lines only.

You might want to rely on your IDE's code style support: some projects include an exported configuration.
`reactor-netty` uses `editorconfig` for instance.

If you cannot find any particular instructions below, `reactor-core` style would be a good default for most reactor projects.

#### Reactor-Netty code style configuration

If your editor supports [editorconfig](https://editorconfig.org/), then it should pick up formatter configuration automatically.

That standard is pretty narrow in scope, but allows custom parameters to be added to the config file.
`IntelliJ` has way finer formatter configuration, which it can write to / read from the editorconfig file.
It is the case for reactor-netty.

#### Reactor-Core code style configuration

Eclipse users can import the content of `$PROJECT_DIR/codequality/eclipse`

IntelliJ users can import the xml from `$PROJECT_DIR/codequality/idea`.

IntelliJ users: If your IDE doesn't support import of xml files
(versions prior to 2016.1) you can copy manually into
`$HOME/.IntelliJIdea{version}/codestyles`

### License Headers
#### Add Apache license header to all new classes

```java
/*
 * Copyright (c) 2021 VMware Inc. or its affiliates, All Rights Reserved.
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *        https://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */

package ...;
```

#### Update Apache license header in modified files as necessary

Always check the date range in the license header. For example, if you've
modified a file in 2021 whose header still mentions Pivotal and/or an end year,
like in the examples below:

```java
/*
 * Copyright (c) 2011-2015 Pivotal Software Inc, All Rights Reserved.
 * Copyright (c) 2011-Present Pivotal Software Inc, All Rights Reserved.
 */
```

Then be sure to update it to:

```java
/*
 * Copyright (c) 2011-2021 VMware Inc. or its affiliates, All Rights Reserved.
 */
```


## :mortar_board: Learning more about the tools we use

### Pull-Requests
Not sure what a pull request is, or how to submit one? Take a look at GitHub's
excellent [help documentation](https://help.github.com/categories/collaborating-with-issues-and-pull-requests/) first.

Follow the same conventions for pull request subject lines as mentioned above
for commit message subject lines.

In the body:

1. Explain your use case. What led you to submit this change? Why were existing
   mechanisms in the framework insufficient? Make a case that this is a
   general-purpose problem and that yours is a general-purpose solution, etc.
1. Add any additional information and ask questions; start a conversation or
   continue one from the original GitHub issue.
1. Mention the Github issue ID if there is one.

Note that for pull requests containing a single commit, GitHub will default the
subject line and body of the pull request to match the subject line and body of
the commit message. This is fine, but please also include the items above in the
body of the request.

### Squashing Commits
To learn more about these techniques, like `git rebase --interactive --autosquash`,
`git add --patch`, and other tools to "squash" multiple commits into a single
atomic commit, in addition to the man pages for git.
The [Rewriting History section of Pro Git](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)
provides a good overview about these tools.
