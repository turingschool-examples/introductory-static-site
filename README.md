---
title: Intro to HTML and CSS Static Site Project
length:
tags: html, css
---

### Goals

By the end of this tutorial, you will know/be able to:

* Have an understanding of how to write well constructed, semantic HTML
* Understand how to control the positioning of HTML elements on your page using CSS
* Gain clarity no how CSS is used to create your layout

### Building a Static Site

#### Hook: <5 min

HTML and CSS are used everywhere on the web, and engaging and appealing pages can be built with a surprisingly small amount of code.

#### Opening: 1-2 min

* What is this lesson about?
* What will students know or be able to do by the end of the class? What are the goals?

#### Start with the Structure

Just like you wouldn't build a house without framing the walls first, it's a good idea to write up the basic HTML structure of your site before you begin to add content and style your page.

Before we write any code, we need to set up our directory structure. Make a new project folder called "dog-party", and inside of that put the following things:

* a file named ```index.html```
* a file called ```styles.css```
* a file called ```reset.css```
* a folder called "images" to hold all the images for the site

Now, let's take a look at the site we want to build:

![Image of Dog Party Site](../images/example/main-page.png)

From this screen grab we can see that we have the following elements:

* a primary header bar with navigation
* a hero unit with a full width background image, title, and call to action button
* three columns with secondary content, images, and buttons
* a footer

The first thing we'll do is break this layout down into semantic HTML tags to help us clarify how we want to build the page. That seems pretty straightforward! Let's write up the skeleton HTML so we have a roadmap to follow as we work.

```HTML
<!doctype html>
<html>
  <head>
  </head>

  <body>
    <header>
      <nav>
        <h1></h1>
        <ul>
          <li></li>
          <li></li>
          <li></li>
        </ul>
      </nav>
    </header>

    <section></section>

    <section>
      <article></article>
      <article></article>
      <article></article>
    </section>

    <footer></footer>
  </body>
</html>
```

Let's walk through this from the top down: you can see that we have a ```<header>``` tag for our primary header, and within that we have an ```<h1>``` that will become our logo, and a  ```<nav>``` tag that's holding an unordered list that will become our primary navigation links.

Then, we have an empty ```<section>``` tag that will become our hero unit.

Below that, we have another ```<section>``` tag with three ```<article>``` tags. These will become our 3 columns.

And, finally, we have a ```<footer>``` tag.

Now that we have our roadmap, let's add a little placeholder content so we can open this up in our browser and take a look:

```HTML
<!doctype html>
<html>
  <head>
    <title>Dog Party</title>
  </head>

  <body>
    <header>
      <nav>
        <h1>Dog Party!</h1>
        <ul>
          <li>one</li>
          <li>two</li>
          <li>three</li>
        </ul>
      </nav>
    </header>

    <section>
      <h2>A Site About Some Dogs</h2>
    </section>

    <section>
      <article>one</article>
      <article>two</article>
      <article>three</article>
    </section>

    <footer>
      <h4>footer</h4>
    </footer>
  </body>
</html>
```

Open your index.html file in your browser and take a look. It doesn't look like much yet, but we can see that the content hierarchy and structure makes sense.

![Image of Dog Party Site](../images/example/road-map.png)

Looking at this unstyled HTML, we can see that the browser has applied default styles for us. That was nice of them! But, as we write our own styles for this page, these defaults could get in our way and make us write extra code. So, let's pull in a reset file to zero out these styles so we can start with a blank slate. The good news is that there are several open source reset files we can use. [Go to this site](http://meyerweb.com/eric/tools/css/reset/), and copy the code for the reset file (remember to include the lines of code crediting Eric Meyers, the developer who wrote this!). Now, back in your project, paste this code into ```reset.css```. Since this code is clearing out all the default styles for us, it's a good idea to keep it organized in it's own file. That way we can keep our ```styles.css``` file dedicated to the new styles we write.

Back in the browser, refresh you page. What do you see?

Huh. It looks the same. Why isn't the reset file doing anything?

We haven't connected our HTML and our CSS! It's an easy fix. In the ```<head>``` tag of our site, let's add the link to the CSS file:

```HTML
<link rel="stylesheet" type="text/css" href="css/reset.css">
```

Now refresh your page again. All the text should be the same size now! That means our HTML and CSS files are working together properly. Since we know we'll need to hook up our custom stylesheet, let's do that now. Add this line *after* the link to your reset file:

```HTML
<link rel="stylesheet" type="text/css" href="css/styles.css">
```

*Note* it's important to put the link to the stylesheet in the  ```<head>``` tag and not the ```<header>``` tag. The ```<head>``` tag is where the metadata for the page goes, which means things like links to stylesheets, fonts, and our page title live there but actual content for the user -- like the navigation elements in our ```<header>``` -- does not.

To double check that our ```styles.css``` is working properly, let's set a loud color as the background on the ```<body>``` tag -- don't worry, we won't leave this color in our styles, we just want to do a quick sanity check to make sure everything is working as expected! In ```styles.css``` add a magenta background to the body:

```CSS
body {
  background-color: magenta;
}
```

Refresh your browser and you should see a very bright page.

![Image of Dog Party Site](../images/example/magenta-page.png)

So, now that we know our style sheet is linked up correctly, let's start styling our page.


##### Making a Navigation Bar




#### Independent/Pair Practice (You do)

* students "doing", instructor available as lifeline
* Examples: questions in a Gist, implementing feature, creating diagram

#### The Closing: ~5 min

* Check for understanding
* Discuss any clarifications or student misconceptions
* Review goals, further resources, and next steps

### Possible questions and/or misunderstandings

* What questions might students ask during class, and how will you respond?
* What concepts might students misunderstand, and why?

### Slides

* [Link to optional slides]()
