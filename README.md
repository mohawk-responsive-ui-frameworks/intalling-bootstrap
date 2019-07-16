# Exercise 1: Installing Bootstrap

In this exercise we're going to install Bootstrap by following instructions from the official documentation. Throughout this exercise you will be expected to follow the official [getting started](https://getbootstrap.com/docs/4.2/getting-started/introduction/) guide while working through the instructions here. Take some time and read up to the [starter template section](https://getbootstrap.com/docs/4.2/getting-started/introduction/#starter-template). Don't worry about copy and pasting any HTML elements or modifying any files in this repository yet.




## Instructions

### Starter Template

Bootstrap's getting started guide comes included with a [starter template](https://getbootstrap.com/docs/4.2/getting-started/introduction/#starter-template) we can use to start any project we plan to use Bootstrap with. Copy paste the contents of the starter template into the `public/index.html` file in this repository.

If successful, upon starting our development server and visiting our local website, we should see a webpage that looks like this:

![The homepage of your website should display after implementing the starter template](readme-assets/starter-template.png)


#### Breakdown

##### doctype
Defines the HTML file as an _HTML 5_ document.

```html
<!doctype html>
```

##### charset
Specifies the character set for the document as _UTF-8_. It's good practice to make this the first child element of `<head>` in any HTML document whether you're using a responsive UI framework or not.

```html
<meta charset="utf-8">
```

##### Responsive Meta Tag
Configures the details of how a webpage is rendered within a browser window. This is particularly useful for mobile devices. As a general rule of thumb, default to the element displayed below and change as required. For further reading see the [resources section](#resources) or [this section](https://getbootstrap.com/docs/4.2/getting-started/introduction/#responsive-meta-tag) of the official documentation.

```html
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
```

##### CSS
This element is including Bootstrap's CSS file. This is the only asset absolutely required in order to install Bootstrap onto your webpage. It's currently downloading the file through a _Content Distribution Network_ (or CDN). This means this file isn't coming from our own computer, but from servers ran by Bootstrap to distribute their framework.

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css" integrity="sha384-GJzZqFGwb1QTTN6wy59ffF1BuGJpLSa9DkKMp0DgiMDm4iYMj70gZWKYbI706tWS" crossorigin="anonymous">
```

##### JavaScript
These elements include all the JavaScript Bootstrap requires in order for all of it's features to properly function. They're the last elements found in a `<body>` element to ensure the elements they'll be operating off of will exist when the JavaScript code is ran.

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js" integrity="sha384-wHAiFfRlMFy6i5SRaxvfOCifBUQy1xHdJ/yoi7FRNXMRBu5WHdZYu1hA6ZOblgut" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js" integrity="sha384-B0UglyR+jN6CkvvICOB2joaf5I4l3gm9GU6Hc1og6Ls7i6U/mkkaduKaBhlAXv9k" crossorigin="anonymous"></script>
```

We're not going to worry about the purpose of the `integrity` and `crossorigin` attributes for this course. They're security measures that make sense when pulling assets from a CDN which we'll be migrating from shortly.

1. [**jQuery:**](http://jquery.com) Bootstrap is written using the jQuery JavaScript library. Due to the popularity of this library, Bootstrap requires you to include it on its own to avoid websites including multiple versions of the library on their webpages.
1. [**popper.js:**](https://popper.js.org/) Just like jQuery, is a library that Bootstrap depends on for its dropdown menus and tooltips.
1. **bootstrap.js:** The actual JavaScript code that's a part of the Bootstrap framework, that relies on both jQuery and popper.js.

***



### Adding a Container

We can see that our webpage as it is has default styles applied to it from Bootstrap. To make further use of the framework we can wrap our `<h1>` in a container.

> Containers are the most basic layout element in Bootstrap and are required when using our default grid system.

[**Source: Bootstrap Documentation**](https://getbootstrap.com/docs/4.2/layout/overview/#containers)

As outlined in their code example we can add a container by wrapping an element around our content with the `container` class name.

```html
<div class="container">
  <!-- Content here -->
</div>
```

Apply what we know now to wrap our `<h1>` with a Bootstrap container. When done correctly your page should look similar to the image below.

![The homepage of your website should display after adding a container](readme-assets/adding-a-container.png)



### Serving Bootstrap Locally

Download the [compiled CSS and JS](https://getbootstrap.com/docs/4.2/getting-started/download/#compiled-css-and-js) and move the appropriate files into the `public/lib` directory:

| **From** | **To** |
| --- | --- |
| `css/bootstrap.css` | `public/lib/bootstrap.css` |
| `js/bootstrap.bundle.js` | `public/lib/bootstrap.js` |

_If there are any inconsistencies with the downloaded assets, you can also grab them from this repository [here](https://gitlab.com/mohawk-responsive-design-frameworks/1-installing-bootstrap/blob/master/readme-assets/bootstrap-4.2.1.zip)._

After moving these two files into their appropriate locations, we need to modify the HTML inside the file `public/index.html`:

1. Remove all existing `<link>` and `<script>` elements
1. Add a `<link>` element at the end of the `<head>` that points to `/lib/bootstrap.css`
1. Add a `<script>` element after the previously added `<link>` that points to `/lib/bootstrap.js`
1. Add the `defer` attribute to the `<script>` element.


#### The `defer` Attribute

`<script>` elements without the `defer` attribute are fetched and executed immediately, before the browser continues to parse the page _[(Source)](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script#Notes)_. Older browsers that have fallen out of popular use weren't able to make use of the `defer` attribute. The older solution to this problem was putting all of the `<script>` elements a page may use as the last children of our `<body>`.

We no longer need to worry about these old browsers and can instead insert our `<script>` elements in our `<head>` with the `defer` attribute. Throughout this course this will be the method of including JavaScript on any webpage you will be expected to implement. You can read more about the `defer` attribute [on MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script#attr-defer).

##### Example
```html
<script src="/lib/jquery" defer></script>
```




## Rubric

1. Is valid HTML5 document ***(2 marks)***
1. `<title>` is in `<head>` and contains the text _My First Bootstrap Page_ ***(1 mark)***
1. Has the following HTML elements:
	1. `<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">` ***(1 mark)***
	1. `<link rel="stylesheet" href="/lib/bootstrap.css">` ***(1 mark)***
	1. `<script src="/lib/jquery.js" defer></script>` ***(1 mark)***
	1. `<script src="/lib/popper.js" defer></script>` ***(1 mark)***
	1. `<script src="/lib/bootstrap.js" defer></script>` ***(1 mark)***
1. HTML document has a has a block level element (`<div>`, `<main>`) with `class="container"` ***(2 marks)***
1. Container has some text inside it ***(1 mark)***

**Total:** _11 Marks_




## Resources

- [MDN: Viewport Meta Tag](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag)
- [Box Sizing](https://getbootstrap.com/docs/4.2/getting-started/introduction/#box-sizing)
