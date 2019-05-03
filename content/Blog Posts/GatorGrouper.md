---
title: "Developing GatorGrouper "

featured_dev_image: "devimage.jpg"

---

![GatorGrader](/images/gatorgrouper_logo.svg)

## Overview

Designed for use with GitHub, GitHub Classroom, and Travis CI, GatorGrouper is an online group creation tool to help facilitate group assignment in an educational setting. While other group management tools create random groups, GatorGrouper supports random and round robin style grouping with the option to specify absentees. With creative implementation through a web application, users can return to the site and update or re-group using previously entered data. It utilizes the Django web framework and accomadates GitHub Classroom where teachers can invites students to create and assign groups.
[here.](https://github.com/GatorEducator/gatorgrouper)

## What I did

To begin this project I collaborated with others in order to form groups and organize tasks. I played a part in creating the requirements handled in the assessment of the project. Later I worked in a team with the task of testing and documentation. I created many test cases utilizing hypothesis which is a type of random parameterized testing. I researched graph theory in order to aid in the creation of a new algorithm to implement into the project, however I returned to creating test cases to obtain complete code coverage.
Below is an example of testing with hypothesis.

```

@given(numgrps=integers(min_value=2, max_value=6))
@settings(verbosity=Verbosity.verbose)
@pytest.mark.hypothesisworks
def test_hypothesis_rrobin_responses(numgrps):
    """Testing the grouping function according to responses with hypothesis"""
    lst = [
        ["Dan", True, True, True],
        ["Jesse", True, True, True],
        ["Austin", True, True, True],
        ["Nick", False, False, False],
        ["Nikki", False, False, False],
        ["Maria", False, False, False],
        ["Jeff", False, False, False],
        ["Simon", False, False, False],
        ["Jon", False, False, False],
        ["Angie", False, False, False],
        ["Izaak", False, False, False],
        ["Jacob", False, False, False],
    ]
    grpsize = len(lst) // numgrps
    response_output = group_creation.group_rrobin_num_group(lst, numgrps)
    assert len(response_output[0]) == grpsize
    assert len(response_output) == numgrps
    assert response_output[0][0][1] is True
    assert response_output[1][0][1] is True
    assert response_output[2][0][1] is True

```

This is creating a random number for the variable numgrps with values specified
at the top of the code. One nice part of this was that there were some test cases
that were already created. So I only needed to adapt what was there with hypothesis.
The work ranged from reusing the previous test cases to completely refactoring code
for a new test case.

## My Experience

I learned so much during this time of development. The very first day of the assignment
our instructer stood in front of the class and told us that he would not organize
anything. We had to figure out, manage, and organize everything on our own. Needless
to say, it was extremely chaotic the first day. I and a few others helped to organize
everyone together. Unfortunately, many people were not familiar with the format of
GitHub so there were a few people pushing to the master branch rather than their
own. This caused problems as people's work were being overwritten. We held a group
meeting and myself and three others worked to revert the state of master to a working
build as well as restore anything that was merged in. There were so many commands, ideas,
and concepts that I had never heard of and I had to figure it out on my own. This meant
I spent a lot of time reading and applying. This was also great exposure to continuous
integration and has helped to solidify and create understandings of concepts.
