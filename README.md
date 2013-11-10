How To Make A Tutorial
============

Welcome to Tut! In this tutorial, we'll show you how to use the Tut system to create and publish a tutorial of your own (so meta!).  We'll begin with a conceptual overview of the Tut system, and then move on into the nuts and bolts of publishing your tutorial.

##The Tut system##

There are two types of user who might use Tut:  _learners_ and _teachers_.  These categories are not mutually exclusive - for instance, if you're taking this tutorial, it's so you can be a teacher yourself.  However, since you are taking a tutorial, right now you are a learner!

There are two main forms of tutorial content:  _study materials_, and _test materials_.  Study materials are things like text or linked video that explain the concept you're trying to convey (you are reading the study materials of this tutorial right now).  Test materials are quiz questions that can be in any of the following formats:  _multiple choice_, _true or false_, or _short answer_.

Learners will navigate your tutorials as follows.  First, they will read the study materials.  Research suggests that an optimal way to study is to absorb content in three intense 10-15 minute study sessions, with a 10 minute break for rest in between.  So, one of the critical features of a good tutorial is that it takes about 10-15 to read through (or watch, it it's a linked video).  If your tutorial is much longer or much shorter than this, you may not receive a very high rating from the Tut community.  Once the user feels they've read over the material enough (hopefully following our guidelines of 3 study sessions, with a 10-minute break in between), they'll click a button on the tutorial screen to indicate that they're reading for the test period to begin.

The test period is a really cool features of Tut.  It's been demonstrated that _distributed testing_, where people answer quiz questions over time is much better than _massed testing_, where people answer quiz questions all in the same test session.  You may have noticed when you created your account that Tut asks you for your mobile number.  This is so we can actually send our learners quiz questions at random times of the day via SMS.   When a learner receives a text from Tut, they text the answer back, and immediately get feedback on whether their answer is right or wrong.  They also receive points based on how quickly they can answer their quiz question.  After the answer is received and feedback is given, another quiz question will be sent at another random time.  If a user chooses to ignore a quiz question, they won't receive any more texts from Tut until it's been answered.  We'll show you how to construct a quiz question in the next section.

##Publishing your tutorial##

The Tut system uses github repositories to act as hosts for tutorials.  This has a lot of advantages, the most important one being that it allows for collaborative editing of tutorials.  So, in order to publish a tutorial, you'll need an account on github.  You'll also want to familiarize yourself with git Markdown, so that you can make your tutorial pretty.

Now, let's go through the steps Let's get into the nuts and bolts of tutorial publishing.  

1 - Tut runs on Node.js and can be installed using the node package manager:

sudo npm install tut

At any time, you can learn about Tut's functions by typing:

tut --help

2 - Let's create our first tutorial (this tutorial in fact), by running:

tut -c how_to_make_a_tutorial -g cbattista

The argument after -c is the name of your tutorial, and the argument after -g is your github username.  

3 - After you create your tutorial, a directory on your local machine should be created.  Go into that directory using:

cd how_to_make_a_tutorial

There will be a file called README.md - this is the file that contains the study materials for your tutorial.
There will also be a file called tut.json - this contains meta-information about your tutorial and your test materials.

4 - Now we need to connect things to github.  Log into github and create a repository with the same name (in my case, it's needs to be called how_to_make_a_tutorial).

5 - Once the git repository is created, obtain the SSH clone URL from git.  Back on your command prompt, run the following commands:

git remote add origin git@github.com:cbattista/how_to_make_a_tutorial.git

git push origin master

6 - At this point, you should have your study materials in README.md, and they can be published using:

tut -p

7 - Anytime you make any changes to tutorial you use the standard git tools to commit your changes.

git commit -a -m "Description of changes"
git push origin master

##The files
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



##How to make tutorial questions

In addition to the study materials, you also need testing materials.  These are located in the file tut.json.  As mentioned, testing materials come in the following formats: _multiple choice_, _true or false_, and _short answer_.

Here's an example of a multiple choice question, in JSON format:
```
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
```
{
   "question":  "True of False?  Massed testing is better than distributed testing."
   "answer": False
}
```

Lastly, here's an example of a short answer question:
```
  {
    "question": "this command line tool can be used to create tutorials",
    "answer": "tut"
  }
```
