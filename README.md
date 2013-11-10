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

1.  Tut runs on Node.js and can be installed using the node package manager:

sudo npm install tut

At any time, you can learn about Tut's functions by typing:

tut --help

2.  Let's create our first tutorial (this tutorial in fact), by running:

tut -c how_to_make_a_tutorial -g cbattista

The argument after -c is the name of your tutorial, and the argument after -g is your github username.  

3.  After you create your tutorial, a directory on your local machine should be created.  Go into that directory using:

cd how_to_make_a_tutorial

There will be a file called README.md - this is the file that contains your tutorial is written in.

4.  Now we need to connect things to github.  Log into github and create a repository with the same name (in my case, it's needs to be called how_to_make_a_tutorial).

5.  Once the git repository is created, obtain the SSH clone URL from git.  Back on your command prompt, run the following commands:

git remote add origin git@github.com:cbattista/how_to_make_a_tutorial.git
git push origin master

6.  At this point, you should have your study materials in README.md, and they can be published using:

tut -p
