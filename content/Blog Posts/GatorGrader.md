---
title: "Developing GatorGrader "

featured_dev_image: "devimage.jpg"

---
## Overview

![GatorGrader](/images/gatorgrader.png)

GatorGrader is a tool designed to be used with GitHub, GitHub Classroom, Travis CI,
and Gradle, another tool in GatorEducator. It is designed for automatic assessment
of programmers and writers. You can find the GitHub documentation
[here.](https://github.com/GatorEducator/gatorgrader)

## What I did

I worked on a team of five people in order to add a new feature that would
obtain issues from the GitHub issue tracker. I implemented code to link the
GatorGrader code to GitHub in order to retrieve issues which can be seen here.
```
from github import Github
from github.GithubException import UnknownObjectException, BadCredentialsException
```
These two lines are important for connecting the program to GitHub and any
exceptions that may occur along with it. Next we have a method I helped to create:
```
def check_comments_made(token, repo, name, expected, issue_state):
    """Returns the number of comments that the given user has made"""
    # github access
    g = Github(token)
    # gets the repo
    try:
        repo = g.get_repo(repo)
    except BadCredentialsException:
        return False, 0, -1
    except UnknownObjectException:
        return False, 0, -2
    comments_made = 0
    for issue in repo.get_issues(state=issue_state):
        for comment in issue.get_comments():
            if comment.user.login == name and issue.pull_request is None:
                comments_made += 1
            if comments_made >= expected:
                return True, comments_made, 0
    return comments_made >= expected, comments_made, 0
```
Of course, this is missing a few pieces with this code. For this to work, the
variable `token` needs to have an actual GitHub token before it would work.
Then I worked with one of my colleagues to implement the retrieval of issues
based on user specifications. I also touched on the implementation of testing for
the issue tracker in order to obtain high code coverage, however, one of my
colleagues did all of them overnight. Thankfully there were a few test cases
that he did not cover so I was able to work and implement more test coverage
for `invoke.py`

## My Experience

I had an amazing experience working on this project. I learned a lot from this
software project and I learned how much one can learn from good documentation.
As I mentioned in the section prior to this, one of my colleagues did all of the
test cases overnight. Unfortunately this was a common case throughout the whole project.
I appreciate him and his work, however, he often said he was, "bored" and he messaged
the team one night and said, "I'm sorry if I stepped on anyone's toes, but I
finished everything." This was an excellent learning experience for me as well.
I learned the importance of communication and I am learning about what to do
in the future to prevent incidences like this from occurring in the future so
that we can all split the work evenly.
