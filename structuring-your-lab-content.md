## Qualities of a Good Lab

### Naming Convention

Naming convention is helpful for instructors to at a glance know what a lab is covering and if it should be assigned. MLabs should be named to correspond with the Topics defined on Learn. It should at the very least begin with the name of the Topic. The last word should be lab (to distinguish it from a Readme) So for example:

* "Rails-Blog-Nested-Resources-lab"
* "SQL-Library-lab"
* "Sinatra-Nested-Forms-lab"
* "js-oo-task-list-lab"


### Content

Ideally, a lab should focus on one Readme. Of course, many of our labs require students to practice more than one skill, especially in more complex full application labs. But most effective labs are granular, because they allow a student to hone in and focus on one skill.

Try to keep your labs focused to one lesson. For Rails and more complex topics such as Angular and Express, our labs should be granular, with each iteration building off the preceding one. An example of this is the Rails Blog Domain, which is comprised of the following labs, all of which are iterations on top of the preceding lab:

1. Rails Blog Scaffold
2. Rails Blog Associations Validations
3. Rails Blog Nested Forms
4. Rails Blog Nested Resources
5. Rails Blog Sessions
6. Rails Blog Omniauth
7. Rails Blog Asset Pipeline

#### Purpose

Labs are for students to be practicing what is taught in a lecture or through reading. Students become developers when they are working on labs.

Because of this, we want our labs to be challenging but applicable. Students should feel pushed intellectually with each lab, but not overwhelmed.

For this reason, our overall curriculum should include labs of **varying degrees of difficulty**. For important Units or Lessons, we should make sure that there are Introductory, Intermediate, and Advanced labs. This also creates flexibility on a semester-by-semester, or even student-by-student basis: we can deploy lab(s) applicable for individual learning paces.


### Readme

Your lab's Readme is the first point of reference about your lab to a student. And, if you're making a tutorial or resource that isn't a full lab, your Readme is everything.

#### Objectives

Objectives are most likely the first thing a student will see when looking at a lab Readme. Oftentimes, your objectives can match the objectives from the preceding Readme if the lab is designed to test the skills and knowledge covered in that lesson. Other times, your objectives can be taken from variouse Readmes if the lab is designed to be more cumulative and expansive.

#### Readme Content

A good Readme accomplishes the following:

* The student should know right away what the lab is about. Be sure to clearly introduce the lesson right away.
* Lists the tasks the student must complete to satisfy the lab.
  * These instructions should be clear enough without giving away too much to the student.
* Gives deliverables (for example, which tests must be passed, or which tests need to be finished by the student)
* Has helpful, short resources, which could be anything you think might help and enhance the student's learning (examples: blog posts, conference talks, chapters or sections from programming books from our library).
* Is clearly written, and very explicit: avoid words like "it", "this", "these", etc. Take nothing for granted in your explanation of new topics.
  * If this lab is introducing something new (something that has not be covered yet in lecture), the Readme can be more handholding in regards to the new material. In general, however, avoid covering a lot of new information in a lab as new content should be reserved for the Readmes. 
* Bonuses, if applicable:
  * A screenshot of the desired outcome
  * a demo (if it's a Rails app, think about deploying your solution to Heroku; the flatiron-rails gem makes this easy)
  * a screencast explaining an important concept pertaining to the lab

### Solution Branch

Your solution branch should have a clean, understandable solution that other instructors can refer to for lab reviews and helping students. Sometimes, students might want the solution pushed up to them after they've completed the lab, so it's important that the solution is straightforward.

