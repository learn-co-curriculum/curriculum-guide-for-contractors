# Mechanics

There are a few things that require a few steps to get up and running:

+ .learn file

+ Adding an image or gif to your Readme

## .learn file

The `.learn` file makes our curriculum searchable. It's important to add proper tags to this file so that we know the languages uses, and skills addressed.

A typical `.learn` file looks something like this:

```
tags:
  - arrays
  - CRUD
  - basic arrays
languages:
  - Ruby
resources:
  - 0
type:
  - lab
```

This file is written using YAML, a human readable data serialization format. You can read more about YAML [here](http://docs.ansible.com/ansible/YAMLSyntax.html). It's important to note the `:` after the grouping name. It's equally important to not the space between the `-` and the tag or language name. Without this space, the piece of  curriculum can't be added to track on Learn.co.

### Tags

The tags are a list of all the topics the lab or lesson addresses. If you're working a basic Ruby lab that deals with arrays, iteration, indexes, you would want to include those as your tags.

### Languages

The languages section is all the langauges the student will practice in the lesson or lab. A frontend lab might have several languages:

```
languages:
  - HTML
  - CSS
  - jQuery
  - JavaScript
```

### Resources

Resources holds an integer, the number of resources listed in the lesson or lab. It's ok if your lesson or lab doesn't have any resources.


### Type

The type section lets us mark the category of curriculum. Is it a lab? A code-along? A lesson?

### Important Additional Keys

Most of the entries a `.learn` are just notes. There are a few, however, that will trigger special behaviors on Learn — namely, triggering assessment mode and triggering project mode.

#### Live Assessments

To turn a lesson into a live assessment, simply assign a truthy value to a `live_assessment` key:

``` yaml
live_assessment: 1
```

#### Project Mode

To turn a lesson into a project, simply assign a truthy value to a `project` key:

``` yaml
project: 1
```
