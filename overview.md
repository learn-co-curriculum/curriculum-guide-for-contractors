## What Do We Mean When We Say Curriculum? 

Every individual piece of curriculum is called a Lesson. 

A **Lesson** can be either a Readme or a Lab. Each lesson is stored in its own repository on Github. 

A **Readme** is expository material that describes one or more concepts. Readmes can include exercises for the student to practice, but they’re optional and we’re not testing to see whether the student has successfully passed it.

A **Lab** is more complicated and a student cannot advance to the next lesson unless she has successfully completed and submitted a lab. All of our coding challenges are test driven so you must create tests that a student’s solution needs to pass. The file structure of a lab will vary depending on the type of lab and the topic you’re teaching.

## Are There Files Though That Are Common to Every Lesson? 

Yes. Every lesson repository in Github has **Contributing, License, and .learn** files. 

The contributing file contains info on how to raise issues on a repo. The license file contains our copyright information. These two files are the same no matter what the lesson content is. 

The .learn file is where you include tags to describe what’s covered in the lesson and this will vary depending on the lesson. 
 
In order to avoid manually creating these files every time you make a new lesson, we created a gem you install and run. 

Run "gem install learn_writer"
Type  "learn-write" from the  command line in any directory where you want to create those files 

The files will be created and the only thing after that you'll have to update is the .learn file in Github.

### The .learn file

There are three categories of tags. One is simply called tags. Another is language, and the last is resources. Our ultimate goal with these tags is to make curriculum standardized and easily searchable. For now, here are some general tips for tagging. 

1. In languages, do not include rspec/jasmine in the tag unless the lab is explicitly teaching testing (all labs should be test-driven)
2. Refer to the topics, units, and lessons for tagging ideas
3. Be as specific as possible

#### Tagging Usage

Use Case        | Example Tags
----------------|------------------------------
topics/concepts | algorithms, arrays, authorization, methods, computer science, join tables, iteration
frameworks      | rails, sinatra, angular
libraries       | jquery, popcorn.js
orms            | arel, activerecord, sequel, sql

#### Examples of good tagging:

tags: rails, strong params, complex nested forms, fields_for

tags: methods, variable assignment, iteration

tags: jquery, variable scope

## How Lessons are Organized

Lessons can be organized into Units. While a unit can vary in length, at a minimum, they should contain at least two pieces of content (a Readme and a Lab). 

A series of units can be combined to form a Topic. 

One or more connected Topics create a Track.
