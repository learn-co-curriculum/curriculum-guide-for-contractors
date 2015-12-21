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


## Adding An Image or Gif

Images and gifs are great additions to curriculum. They make the curriculum instantaneously fun, and breakup the monotony of white page with black text.

But you can't just find a great image of a baby hugging a puppy online and use the that URL like this:

```
![Baby Hugging Puppy](http://ak-hdl.buzzfed.com/static/enhanced/webdr01/2013/4/9/17/enhanced-buzz-29534-1365542139-15.jpg)
```

Because what if ak-hd.buzzfeed.com took down that amazing image?! We'd suddenly have a broken image in our curriculum. 

So instead of taking the risk, we like to play it safe and upload any images or gifs to Amazon Web Services.


1. Visit [Amazon Web Services](http://aws.amazon.com/)

2. Click on My Account in the top right corner and select AWS Management Console

3. You should be directed to a page to log in. The email address is `logins@flatironschool.com` and the password is `keyv00nA`.

4. Next you'll want to select S3. You'll find it listed as the first selection in the red grouping, under 'Storage & Content Delivery'

5. All Flatiron buckets will appear. You'll want to scroll until you find the 'learn-verified' bucket

6. To upload a photo, select the big blue 'Upload' button in the top left corner of the learn-verified bucket

7. A window should appear for you to select an image from your computer.

8. Once the image has been uploaded, we'll need to change the image permissions so that anyone can view it. Find the image in the list of images on the left, and right click. Select 'Properties'

![Properties](https://s3.amazonaws.com/learn-verified/properties.png)

9. A window should appear, and you'll want to select 'Permissions' and then click 'Add Permissions'

![Permissions](https://s3.amazonaws.com/learn-verified/add_permissions.png)

10. You'll want to fill in Grantee with 'Everyone' and select the check box next to 'Open/Download'

![Open and Download](https://s3.amazonaws.com/learn-verified/open-download.png)


11. Make sure you click save to save the changes you've made. You can find the AWS URL for the image right above the permissions. You can copy that URL and use it anywhere in your markdown!

![AWS URL](https://s3.amazonaws.com/learn-verified/aws-url.png)

