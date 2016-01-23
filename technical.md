---
layout: default
title: Technical Research | ETL for Data Science
---

<a class="btn" href="{{site.baseurl}}/development.html">&lt; Research and Development</a>

# Technical Research

This page details all the technical research we have done (excluding architecture) throughout this project, including third party open-source libraries that may be useful for the final system. Click the buttons below to jump to the corresponding section.

<a class="btn-resp" href="#graphing-libraries">1. Graphing Libraries</a>
<a class="btn-resp" href="#ui-libraries">2. UI Frameworks/Libraries</a>
<a class="btn-resp" href="#deployment">3. Deployment</a>

<a class="anchor" id="graphing-libraries"></a>

## Graphing Libraries

In order to decide upon which graphing library to use, we carried out extensive research on some widely used free and open-source libraries, these included d3.js and plotly.js. As a result we decided to use plolty.js as our graphing library.

### **D3.js**

As stated earlier [D3.js](http://d3js.org) is a JavaScript library for manipulating documents based on data. It helps you visualise data using HTML, SVG, and CSS. It combines powerful visualization components and a data-driven approach to DOM (Document Object Model) manipulation. D3 is also extremely fast, supporting large datasets and dynamic behaviours for interaction and animation. However a major drawback associated with D3 Is that it does not generate pre-determined visuals for you, as a result it is very inefficient to generate charts using it. At the same time it does not always support older web browsers which may be of concern.

### **Plotly.js**

[Plotly.js](http://plotly.js) is a high level, declarative charting library that is built on top of d3.js and stac.gl. One of the main reasons we decided to use plotly.js as our graphing library is because it supports over 20 different chart types, including 3D plots, geographic maps, and statistical charts like density plots, histograms, box plots, and contour plots. 

<div class="imgCapContainer">
    <img src="{{site.baseurl}}/assets/plotlyjs-logo.png" alt="Cleaning Tab"
     class="titleImage narrowImage">
     <br>
     Plotly.js is an open-source graphing library built on d3.js and stac.gl
</div>

Graphs generated using plotly.js are also interactive, this is because plotly.js is built upon stack.gl – an open source ecosystem for rendering interactive 3D and 2D computer graphics within a web browser. It is for this reason that plotly.js graphs support interactions such as click-and-drag to zoom into a region, double-click to auto scale, click on legend items to toggle traces as well as other operations. It is also worth mentioning that most plotly graphs are drawn with SVG (Scalable Vector Graphics). This offers great compatibility across browsers.

Finally plotly.js charts are described declaratively as JSON objects, and every aspect of the chart, such as colours, grid lines, and the legend, has a corresponding set of JSON attributes. This approach makes it simple to plot a chart as all that is required is a JSON specification of the chart, it also makes the charts language agnostic.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="ui-libraries"></a>

## UI Frameworks/Libraries

As the user interface is not the main focus of this project, we decided to utilise an existing UI framework develop the UI for the front-end of our system. We believe that this will speed up the development of the system and gives us more time and effort to work on the back-end features. 

We decided that we will be using the Material Design language for our UI. Material Design is a visual language that was developed by Google and put emphasis on using material as the metaphor; using bold, graphic, intentional elements; and using motion to provide meaning. We believe that this is a good choice not only because it is a rigid  design language, but also because there is a huge collection of UI frameworks based on the Material Design specification. This meant that we were able to choose the one that is most suitable for this project. We considered several of such frameworks, including Material Design Lite, Materialize, and Angular Material.

### **Material Desing Lite & Materialize**

Both [Material Design Lite](http://www.getmdl.io/index.html) (MDL) and [Materialize](http://materializecss.com) can be used by importing their custom CSS and JavaScript files. The CSS files define custom classes which can be applied to HTML elements to achieve different visual appearences. For example, the following HTML code will create a button:

{% highlight html %}
<!-- Using Material Design Lite -->
<button class="mdl-button mdl-js-button">
  Button
</button>

<!-- Using Materialize -->
<a class="waves-effect waves-light">Button</a>
{% endhighlight %}

As they only consist of custom CSS and JavaScript files, MDL and Materialize has the advantage of being independent from the web-application frameworks, so any change in the architecture regarding the front-end web-app framework will have little to no effect on the work done on the UI using these frameworks.

On the other hand, however, since these frameworks relies on CSS classes only to style the HTML elements, the class declaration for the elements can become unwieldy as the number of classes it belongs to increases to achieve a certain appearance. For example, a button with ripple effects is done by adding multiple classes to the button element in MDL:

{% highlight html %}
<button class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect">
  Get Started
</button>
{% endhighlight %}

MDL is maintained by Google and Materialize was created by a team of students from Carnegie Mellon University. MDL is licensed under an Apache-2 license and Materialize is licensed under an MIT license.

### **Angular Material**

[Angular Material](https://material.angularjs.org/) is a UI library that depends on AngularJS as the name suggests. This alone makes it a compelling choice for our project as we have decided, when designing the system architecture, to use AngularJS as the front-end web-app framework. 

Instead of relying on declaring CSS classes on HTML elements, Angular Material allows the use of directives. This makes it a lot easier to manage the HTML code. For example, creating a button only requires this line of code:

{% highlight html %}
<md-button>Button</md-button>
{% endhighlight %}

Another advantage of Angular Material over MDL and Materialize is that Angular Material supports over 30 UI components while MDL only supports about 15.

In the end, we decided to use Angular Material over MDL or Materialized as we think it is more flexible due to the fact that it takes advantage of the features AngularJS provides.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="deployment"></a>

## Deployment

Since our final product will be a web application with a somewhat complex backend architecture, we need to provide a way for users to access the application. The standard approach is hosting the application publicly and having it accessible on the Internet, but not only would that introduce issues such as security, performance and scalability, it is not the way our client envisioned the application. Instead, they wanted a system that users can setup and run locally. 

Of course, we cannot burden users with the tedious task of manually deploying the system themselves, as that would entail installing, setting up and configuring all the dependencies needed to duplicate the environment needed to serve the application. The solution, suggested by our client, is to use a virtual development environment tool such as Vagrant or Docker. With this method, the user only needs to download and run a VM (VM) that already contains all the components of our application installed, configured and running. 

<div class="imgCapContainer">
    <img src="{{site.baseurl}}/assets/vagrant.png" alt="Cleaning Tab"
     class="titleImage narrowImage sideImage">
     <br>
     Vagrant creates and configures virtual development environments.
</div>

We decided to use Vagrant for virtual deployment. It uses the Oracle VirtualBox hypervisor by default, and supports multiple platforms including Windows, OS X and Linux. The only requirement for deploying with Vagrant is that the user has Vagrant installed on his/her system.

We currently have a demo of a deployment process that uses Vagrant. For the demo, we are using Ubuntu as a base VM, and a provisioning script in bash installs and configures dependencies on startup. Vagrant automatically performs port mapping, allowing the user to access the application on a port on his/her host machine. 

In our deployment demo, the update process is quite inconvenient for the user, as the user must pull changes from the GitHub remote, which changes the contest of the directory containing the web application inside the VM. Our current approach of using a default base box such as Ubuntu and running provisioning scripts thus does not handle updates well and is also quite slow to start up, so we will eventually start creating and hosting our own custom VM images once we are ready for our first release next term. With this configuration, Vagrant would download our custom VM images from our server, and run the VM without the need for provisioning. Vagrant would also handle updates on behalf of the user by automatically checking and downloading any available new releases of our VM. 

<br><a class="btn-resp" href="#top">^ Back to Top</a>