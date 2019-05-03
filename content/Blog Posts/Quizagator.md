---
title: "Developing Quizagator "

featured_dev_image: "devimage.jpg"

---

## Overview

Quizagator is an online tool that allows the creation of tests to be made
through text based syntax as opposed to using a GUI. This means that a
quiz can be created through the use of a text editor. This allows the
creation of tests to be much simpler as there is no need to alter
the quizzes in the GUI tools. This system is created using Flask and
Python along with the use of a SQLite3 database which manages the quizzes
and results. A link to the project can be found
[here](https://github.com/GatorEducator/quizagator)

## What I did.

I had created the base for this project. The base for the project created in Flask
was my Senior Thesis project. From this point, I started working in a team to
create a better system for teachers to create quizzes. To do this, I acted as
a team leader for the Flask development team. I instructed and overlooked, and led
the team in order to ensure a deployable product at the end of the working period.
I also worked to create test cases to increase code coverage. I was also in charge
of helping to review code so that it could be merged with minimal conflicts.

```
@app.route("/teachers/quizzes/set/", methods=["POST"])
@db.validate_teacher
def set_quiz():
    """ Displays a quiz using csv data """
    question = query_db(
        "SELECT questions.id, questions.type")
    # creates each question, one at a time
    item = []
    while question[0][0] is not None:

# call respective method based on question type integer

# OPEN ENDED
        if question[0][1] = 0:
            question_oe = query_db("SELECT question_text, FROM questions WHERE quiz_id=?",
                                   [quiz_id])
            item.append[]

            # return flask.redirect("/teachers/questions/create/<quiz_id>/oe/")

# MULTIPLE CHOICES
        elif question[0][1] = 1:
            questions_db = db.query_db(
                "SELECT question_text, correct_answer, a_answer_text, b_answer_text, "
                "c_answer_text, d_answer_text FROM questions WHERE quiz_id=?;",
                [quiz_id],
            )
            quest_choice = {}
            quest_choice["text"] = question[0]
            quest_choice["correct"] = ["A", "B", "C", "D"][question[1]]
            quest_choice["a"] = question[2]
            quest_choice["b"] = question[3]
            quest_choice["c"] = question[4]
            quest_choice["d"] = question[5]
            item.append(quest_choice)

# RENDER TEMPLATE
        return flask.render_template(
            "/teachers/quiz_page.html",
            items=items,
            quiz_name=quiz_name[0][0],
            quiz_id=quiz_id,


        else:
            flask.flash("There was an error with a question type. Please check for mistakes.")
            return flask.redirect("/teachers/quizzes/")
    return flask.redirect("/teachers/quizzes/")
```

This code is responsible for appending the questions so that it can be displayed
to either the students or the teacher. This is taking in a query to place into
the database to fetch information about question name and id. After getting this
it checks to see what type of question it is. This is done using a boolean value.
If the id is 0 then it assumes it is an open ended question and appends the question
with the appropriate logic. The same is true for when the id is 1. Then it runs
logic for multiple choice questions displaying the name and choices for the problem.
