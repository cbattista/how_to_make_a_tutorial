The tut Package Registry
============

[tut](http://rock-em-sock-em.2013.nodeknockout.com/) is a package registry for discovering and publishing programming tutorials.

Publishing a Tutorial
---------------------

tut is similar to a package registry, such as npm or rubygems, with a key difference

* *tut is designed for publishing tutorials, rather than software packages.*

Here's the steps involved in creating your first tutorial:

* install tut using npm, and use it to generate a tutorial:

```bash
sudo npm install tut -g
tut -c the_tut_package_registry -g my-github-username
```

* tut will create a new github repo that contains two files:
  * *tut.json:* this provides meta-information about your tutorial: questions, answers, a description, a link to the github repo where the tutorial will be hosted.
  * *README.md:* write your tutorial here, using Markdown, feel free to create more Markdown files as you see fit.

* Once you've created your awesome tutorial, create a github repo with the same name for hosting ist
  * as an example, this tutorial is hosted here: https://github.com/cbattista/how_to_make_a_tutorial
  * make sure that there's a corresponding link in your tut.json, in this case *cbattista/how_to_make_a_tutorial*.

* Add this github repo as a remote to your local tutorial:

```bash
git add remote origin git://path-to-tutorial-on-github
```

* Push your up-to-date tutorial to github:

```bash
git push origin master
```

* Register the update with tut:

```bash
tut -p
```

Publishing Updates
------------------

To publish an update to your tutorial, simply:

* increment the version # in tut.json.

* push your updated changes to github:

```bash
git commit -a -m "publishing new version of tutorial."
git push origin master
```

* register the update with tut:

```bash
tut -p
```

The Tut system
--------------

There are two types of user who might use Tut:  _learners_ and _teachers_.  These categories are not mutually exclusive - for instance, if you're taking this tutorial, it's so you can be a teacher yourself.  However, since you are taking a tutorial, right now you are a learner!

There are two main forms of tutorial content:  _study materials_, and _test materials_.  Study materials are things like text or linked video that explain the concept you're trying to convey (you are reading the study materials of this tutorial right now).  Test materials are quiz questions that can be in any of the following formats:  _multiple choice_, _true or false_, or _short answer_.

How learners learn
--------

Learners will navigate your tutorials as follows.  First, they will read the study materials.  Research suggests that an optimal way to study is to absorb content in three intense 10-15 minute study sessions, with a 10 minute break for rest in between.  So, one of the critical features of a good tutorial is that it takes about 10-15 to read through (or watch, it it's a linked video).  If your tutorial is much longer or much shorter than this, you may not receive a very high rating from the Tut community.  Once the user feels they've read over the material enough (hopefully following our guidelines of 3 study sessions, with a 10-minute break in between), they'll click a button on the tutorial screen to indicate that they're reading for the test period to begin.

The files
-------

In your tutorial directory you'll see two files:  README.md and tut.json.  README.md is a git markdown file and is where you should place your study materials (you are reading the README.md file for this tutorial right now).

The second file, tut.json, contains meta-information about your tutorial as well the test materials for your tutorial.  Let's take a look at the meta-information first.

```
	"name": "how_to_make_a_tutorial",
	"title": "How To Make A Tutorial",
	"description": "In this tutorial we'll teach you how to create and publish tutorials using the tut system",
	"version": "0.0.1",
	"github_path": "cbattista/how_to_make_a_tutorial",
	"difficulty": 1,
	"topics": [
  "tut"
]
```

_Name_, _title_, and _description_ should all be pretty self-explanatory.  Make sure this information is accurate, otherwise learners will be confused and/or angry when your tutorial doesn't meet their expectations.

Two other important fields that provide information to the learners are _difficulty_ and _topics_ fields.  Difficulty is rated on a scale of 1 to 10, with 1 being the easiest, and 10 being the hardest.  Remember that we suggest that your study materials should take about 10-15 minutes to read or watch.  If your tutorial requires a lot of background knowledge to be understood in 10-15 minutes time, then you should assign it a high difficulty rating to reflect this.  The topics field is fairly obvious,


Pay close attention to the _version_ field.  This needs to be changed everytime you publish your tutorial.  Tut will not allow you to publish a new version of your tutorial if you haven't updated this field.


The test period is a really cool features of Tut.  It's been demonstrated that _distributed testing_, where people answer quiz questions over time is much better than _massed testing_, where people answer quiz questions all in the same test session.  You may have noticed when you created your account that Tut asks you for your mobile number.  This is so we can actually send our learners quiz questions at random times of the day via SMS.   When a learner receives a text from Tut, they text the answer back, and immediately get feedback on whether their answer is right or wrong.  They also receive points based on how quickly they can answer their quiz question.  After the answer is received and feedback is given, another quiz question will be sent at another random time.  If a user chooses to ignore a quiz question, they won't receive any more texts from Tut until it's been answered.  We'll show you how to construct a quiz question in the next section.

Writing Tutorial Questions
------------------------------

In addition to the study materials, you also need testing materials.  These are located in the file tut.json.  As mentioned, testing materials come in the following formats: _multiple choice_, _true or false_, and _short answer_.

Here's an example of a multiple choice question, in JSON format:

```json
{
    "question": "how long should it take someone to read your tutorial?",
    "options": [
      "15 minutes",
      "1 hour",
      "30 minutes",
      "2 hours"
    ],
    "answer": "15 minutes"
  }
```

Here's a true or false question:

```json
{
   "question":  "True of False?  Massed testing is better than distributed testing."
   "answer": False
}
```

Lastly, here's an example of a short answer question:

```json
  {
    "question": "this command line tool can be used to create tutorials",
    "answer": "tut"
  }
```
