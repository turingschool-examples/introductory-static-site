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

* a file named `index.html`
* a file called `styles.css`
* a file called `reset.css`
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
      <h1></h1>
      <nav>
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

Let's walk through this from the top down: you can see that we have a `<header>` tag for our primary header, and within that we have an `<h1>` that will become our logo, and a  `<nav>` tag that's holding an unordered list that will become our primary navigation links.

Then, we have an empty `<section>` tag that will become our hero unit.

Below that, we have another `<section>` tag with three `<article>` tags. These will become our 3 columns.

And, finally, we have a `<footer>` tag.

Now that we have our roadmap, let's add a little placeholder content so we can open this up in our browser and take a look:

```HTML
<!doctype html>
<html>
  <head>
    <title>Dog Party</title>
  </head>

  <body>
    <header>
      <h1>Dog Party!</h1>
      <nav>
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

Looking at this unstyled HTML, we can see that the browser has applied default styles for us. That was nice of them! But, as we write our own styles for this page, these defaults could get in our way and make us write extra code. So, let's pull in a reset file to zero out these styles so we can start with a blank slate. The good news is that there are several open source reset files we can use. [Go to this site](http://meyerweb.com/eric/tools/css/reset/), and copy the code for the reset file (remember to include the lines of code crediting Eric Meyers, the developer who wrote this!). Now, back in your project, paste this code into `reset.css`. Since this code is clearing out all the default styles for us, it's a good idea to keep it organized in it's own file. That way we can keep our `styles.css` file dedicated to the new styles we write.

Back in the browser, refresh you page. What do you see?

Huh. It looks the same. Why isn't the reset file doing anything?

We haven't connected our HTML and our CSS! It's an easy fix. In the `<head>` tag of our site, let's add the link to the CSS file:

```HTML
<link rel="stylesheet" type="text/css" href="css/reset.css">
```

Now refresh your page again. All the text should be the same size now! That means our HTML and CSS files are working together properly. And since we know we'll need to hook up our custom stylesheet, let's do that now. Add this line *after* the link to your reset file:

```HTML
<link rel="stylesheet" type="text/css" href="css/styles.css">
```

*Note* it's important to put the link to the stylesheet in the  `<head>` tag and not the `<header>` tag. The `<head>` tag is where the metadata for the page goes, which means things like links to stylesheets, fonts, and our page title live there but actual content for the user -- like the navigation elements in our `<header>` -- does not.

To double check that our `styles.css` is working properly, let's set a loud color as the background on the `<body>` tag -- don't worry, we won't leave this color in our styles, we just want to do a quick sanity check to make sure everything is working as expected! In `styles.css` add a magenta background to the body:

```CSS
body {
  background-color: magenta;
}
```

Refresh your browser and you should see a very bright page.

![Image of Dog Party Site](../images/example/magenta-page.png)

So, now that we know our style sheet is linked up correctly, let's begin styling our page. We'll start at the top and work our way down.


##### Making a Navigation Bar

The first element we see is the header bar at the top of the page. We can see that we have a logo on the left side and three links on the right side.

We've written the html structure for this section:

```html
<header>
  <h1>Dog Party!</h1>
  <nav>
    <ul>
      <li>one</li>
      <li>two</li>
      <li>three</li>
    </ul>
  </nav>
</header>
```

First thing first, let's pull in the font we want to use. Let's use [Raleway](). We'll add two lines of code, one in the `<head>` of our index.html file and another in our styles.css:

Add this in the `<head>` of index.html
```html
<link href="https://fonts.googleapis.com/css?family=Raleway" rel="stylesheet">
```

and this in styles.css (we specify the font in the `<body>` tag because we want this to be the font that is used for all text on our page):

```css
body {
  font-family: 'Raleway', sans-serif;
}
```

We know that we want to have a colored header bar, so that is a good starting place to start. Let's do that in our CSS.

```CSS
header {
  background: #92E0E5;
}
```

Great! Our header bar is a nice teal. Next, we know that we want the three links to be on the far right side but they're currently over on the left side under the `<h1>` text. Let's go ahead and move them over. There are several different ways to accomplish this, but for now we'll float it to the right. This will pull the `<nav>` out of the normal page flow and push it over to the right. We write it like this:


```CSS
header nav {
  float: right;
}
```

When we reload the page we see that something still not quite right. The `<nav>` has been pushed over to the right, but now it has been pushed a little bit out of the bottom of the header. That's weird, what's going on?

If we inspect the `<h1>` in the browser using our developer tools, we see that it's taking up the entire width of the page and that is resulting in the `<nav>` getting pushed down out of the header. This is because `<h1>` tags are *block level* elements, so by default they will fill the entire row that they are on. We can solve this by floating our header's h1 to the left. This will keep the h1 on the left side of the screen, but it will pull it out of the normal page flow so both the h1 and the nav will be aligned nicely and inside of the header bar. Our CSS for the `<nav>` and `<h1>` looks like this:

```CSS
header h1 {
  float: left;
}

header nav {
  float: right;
}
```

Great! Now let's get those `<li>` elements to be in a row instead of stacked on top of each other. A simple way to do this is change then from block level elements (their default) to inline elements. This will allow them to all sit next to each other on the same row. Here's the code:

```CSS
header h1 {
  float: left;
}

header nav {
  float: right;
}

nav li {
  display: inline-block;
}
```

If we look at our comp we see that we actually have a logo where the `<h1>` text is. We can do this with an approach called "image text replacement". In short, this approach allows you to keep the search engine-friendly h1 text, but swap it out for an image. You can read about the ins and out of this approach [in this oldie but goodie article by Chris Coyier](https://css-tricks.com/header-text-image-replacement/). Let's look at the code and then walk through it:

```css
header h1 {
  float: left;
  text-indent: -9999px;
  background: url(images/dog-icon.svg) no-repeat;
  height: 35px;
  width: 35px;
  margin-top: 8px;
}
```

We still have our `float: left`, but we've added a few more lines: `text-indent` is shoving the actual text of our h1 negative nine thousand nine hundred and ninety nine pixels way off to the left of the screen. We can't see it as users now, but it's still a part of the site content so we get the SEO benefits. Next, we set our dog-icon.svg as a *background image*. Finally, we set the width and height of the h1 itself, so we have a nicely sized icon. Then, we add 8px of margin to the top of the h1 to vertically center the icon in the header.

That looks pretty close! We just need to get those `<li>` elements vertically centered in the header. We can do that by adding padding to them! The code looks like this:

```css
nav li {
  display: inline-block;
  padding: 17px 10px;
}
```

We just added 17px of padding to the top and bottom of each li, and 10px padding to the left and right sides. This centered them vertically in the header and gave them a little breathing room.

For kicks, let's add a hover to those so our users get some feedback as they mouse over them. Let's make the background and text color on the `<li>` change on `:hover`. Here's the code:

```css
nav li {
  display: inline-block;
  padding: 17px 10px;
}

nav li:hover {
  background: #3F8DA7;
  color: white;
}
```

And that's our header!

##### Making a Hero Unit

Next thing to tackle is the hero unit. This may sound like a strange term, but it's common way to describe a large splash section of a landing page. It basically just means that this section is the first one people will see, so it needs to make a great first impression -- it's a hero!

Let's go through what our hero unit layout needs before we start styling. We'll need a full width background image, a big header, a primary image, and a call to action (also referred to as a "CTA") button.

As a first step, let's add an `id` of "hero" to the `<section>` that will be wrapping our hero unit. This will let us target that specific section with our styles, and since it's unique to this section we can use an `id` because we know we won't have another hero unit.

```html
<body>
  <header>
    <h1>Dog Party!</h1>
    <nav>
      <ul>
        <li>one</li>
        <li>two</li>
        <li>three</li>
      </ul>
    </nav>
  </header>

  <section id="hero">
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
```

We'll also need to add the additional content to our `#hero` section.

```html
<section id="hero">
  <h2>A Site About Some Dogs</h2>
  <img src="images/dog1-sq.jpg" alt="hero dog"/>
  <a href="http://corgis-in-space.tumblr.com/" target="_blank">What are Dogs</a>
</section>
```

IF we refresh our page, it doesn't look great. But now that we have our content in index.html, we can start styling it! The first thing to tackle is the full width background image, and because we put our logo into the header as a background image we're familiar with the syntax it shouldn't be too difficult. Let's do that first:

```css
#hero {
  background: url('../images/park.jpg') no-repeat;
  background-size: cover;
  text-align: center;
  padding: 50px 0;
}
```

That looks much better! But what is this CSS doing? On the first line we set our background image to be `park.jpg` and say that it should not repeat (by default, background images want to repeat, or tile, from left to right, top to bottom). On the next line `background-size: cover` tells the image to fully fill the space available automatically, which means that you won't get awkward white space on the sides or bottom as you move between large and small screen sizes. `text-align: center` centers all the content inside of our `#hero` section, including text *and* images, so our content will be neatly aligned in the center of the page. And finally, `padding: 50px 0` sets internal padding of 50px at the top and bottom of the `#hero` section so the content inside has some breathing room and doesn't feel too crowded.

Hmm. Something isn't right. Why are the primary image and CTA link on the same line? If we inspect those elements in the browser, we see that neither is a block-level element. In fact, both `<img>` and `<a>` tags are inline by default. We can easily fix this by setting the `<img>` to `display: block`.

```css
#hero img {
  display: block;
}
```

Now that the image and the CTA link are on different rows, we can style the image. We'll need to re-center it, add a border-radius to make it a circle, and add a border. Here's the code:

```css
#hero img {
  display: block;
  margin: auto;
  border-radius: 50%;
  border: 5px solid #3F8DA7;
}
```

Now, let's make the `<h2>` a bit larger so it looks more like a title!

```css
#hero h2 {
  font-size: 30px;
}
```

We could use some margin on the bottom of the `<h2>` and the primary image. Let's add that.

```css
#hero img {
  display: block;
  margin: auto;
  margin-bottom: 25px;
  border-radius: 50%;
  border: 5px solid #3F8DA7;
}

#hero h2 {
  font-size: 30px;
  margin-bottom: 25px;
}
```

All that's left is styling our CTA link:

```css
#hero a {
  background: white;
  border: 5px solid #3F8DA7;
  color: #3F8DA7;
  padding: 5px 10px;
  text-decoration: none;
}

#hero a:hover {
  padding: 5px 10px;
  background: #3F8DA7;
  color: white;
}
```

Any with that, our hero unit is complete!

##### Making 3 Columns

In our last section, we have three columns that sit side by side. If we look at them, we see that they all have the same structure and content organization. They consist of a title, an image, a block of text, and a button. We know that each column will have the same structure with different content, so we will use the same base HTML and styles for all three and then simply plug in the unique content for each. This let's us keep our code DRY. Let's update our HTML structure first so all three columns are the same:

```html
<body>
  <header>
    <h1>Dog Party!</h1>
    <nav>
      <ul>
        <li>one</li>
        <li>two</li>
        <li>three</li>
      </ul>
    </nav>
  </header>

  <section id="hero">
    <h2>A Site About Some Dogs</h2>
  </section>

  <section>
    <article class="three-col">
      <h3>One</h3>
      <img src="" alt="first image"/>
      <p></p>
      <a href=""></a>
    </article>

    <article class="three-col">
      <h3>Two</h3>
      <img src="" alt="second image"/>
      <p></p>
      <a href=""></a>
    </article>

    <article class="three-col">
      <h3>Three</h3>
      <img src="" alt="third image"/>
      <p></p>
      <a href=""></a>
    </article>
  </section>

  <footer>
    <h4>footer</h4>
  </footer>
</body>
```

If we refresh our page now, not a whole lot has changed. Time to put in content! Let's add images and text. We can grab a few lines of placeholder text from a [lorem ipsum text generator](http://www.catipsum.com/).

```html
  <section>
    <article class="three-col">
      <h3>One</h3>
      <img src="images/dog2-sq.jpg" alt="first image"/>
      <p>
        Nap all day Gate keepers of hell yet stares at human while pushing stuff off a table. Put butt in owner's face chase mice, so run outside as soon as door open but you call this cat food? stare at the wall, play with food and get confused by dust.
      </p>
      <a href="https://en.wikipedia.org/wiki/Dog">Link One</a>
    </article>

    <article class="three-col">
      <h3>Two</h3>
      <img src="images/dog3-sq.jpg" alt="second image"/>
      <p>
        Soft kitty warm kitty little ball of furr. Hunt anything that moves meowing non stop for food stand in front of the computer screen knock dish off table head butt cant eat out of my own dish, then cats take over the world hide when guests come over.
      </p>
      <a href="http://www.dog-adoption-and-training-guide.com/about-dogs.html">Link Two</a>
    </article>

    <article class="three-col">
      <h3>Three</h3>
      <img src="images/dog4-sq.jpg" alt="third image"/>
      <p>
        Destroy the blinds chase imaginary bugs, so lie on your belly and purr when you are asleep. Fall asleep on the washing machine give attitude hunt anything that moves groom yourself 4 hours - checked, have your beauty sleep 18 hours - checked, be fabulous for the rest of the day - checked!
      </p>
      <a href="http://www.livescience.com/13305-facts-dog-breeds-genetics-pets.html">Link Three</a>
    </article>
  </section>
```



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
