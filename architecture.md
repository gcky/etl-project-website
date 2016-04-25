---
layout: default
title: Architecture | ETL for Data Science
---

<a class="btn" href="{{site.baseurl}}/development.html">&lt; Research and Development</a>

# Architecture Research and Design

This page details the research we have done through the course of designing the architecture for our system. Click the buttons below to jump to the corresponding section.

<a class="btn-resp" href="#important-decisions">1. Important Decisions</a>
<a class="btn-resp" href="#first-iteration">2. First Iteration</a>
<a class="btn-resp" href="#alterations">3. Alterations During Development</a>

<a class="anchor" id="important-decisions"></a>

## Important Decisions

<table class="invisible"><tr>
    <td>
        <div class="imgCapContainer">
            <img src="{{site.baseurl}}/assets/angularjs.png" alt="AngularJS"
            class="sideImage"></a>
        </div>
    </td>
    <td>
        <div class="imgCapContainer">
            <img src="{{site.baseurl}}/assets/socketio.gif" alt="SocketIO"
            class="sideImage"></a>
        </div>
    </td>
    <td>
        <div class="imgCapContainer">
            <img src="{{site.baseurl}}/assets/flask.png" alt="Flask"
            class="sideImage"></a>
        </div>
    </td>
</tr></tr></table>

<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #1</strong>
		</td>
		<td>
			Where will processing operations take place?
		</td>
	</tr>
	<tr>
		<td rowspan="2">
			<strong>Options considered</strong>
		</td>
		<td>
			on the user's browser, locally
		</td>
	</tr>
	<tr>
		<td>
			on a backend, remotely
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			on a backend, remotely
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not on the user's browser (locally)?</strong>
			<p>Performing the data processing locally will make for a simpler architecture, but it is a worse option in every other regard. Choosing this approach will make the performance of the end product be bottlenecked by the user's computer and browser capabilities. It also limits development options, as we would most likely only be able to code in JavaScript. Lastly, we would end up with an architecture whose computational capability cannot scale beyond the user's browser. </p>
			<strong>Why on a backend, remotely?</strong>
			<p>Although choosing to introduce a back-end component to the project on which data processing takes place will make the architecture of our product more complex, the benefits outweigh this minor disadvantage. </p>
			<p>Moving data processing to a back-end instead of performing it will overcome all the shortcomings of performing it locally. The end product will have higher performance and an architecture that can scale much more easily. It gives us greater freedom in terms of development, as there are many more choices of platforms for a backend.  </p>
			<p>There is no use avoiding a backend as one of our "could have" requirements is the option for a notebook style interface which would most likely necessitate some form of backend anyway.</p>
		</td>
	</tr>
</table>


<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #2</strong>
		</td>
		<td>
			Which data processing tools/libraries/frameworks will be used in the backend?
		</td>
	</tr>
	<tr>
		<td rowspan="4">
			<strong>Options considered</strong>
		</td>
		<td>
			Apache Spark
		</td>
	</tr>
	<tr>
		<td>
			Pandas
		</td>
	</tr>
	<tr>
		<td>
			R (language) + its built-in libraries
		</td>
	</tr>
	<tr>
		<td>
			no library/a custom implementation
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			Pandas
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not no library/a custom implementation?</strong>
			<p>It would be a waste of time re-inventing the wheel when there are readily available open-source libraries that we can integrate into our project. </p>
			<strong>Why not Apache Spark?</strong>
			<p>Apache Spark is the option that is the most scalable and thus would afford the best performance, as Spark being a cluster computing framework is inherently scalable and designed for performance. However, we were advised by our client that it would be overkill for our project and that such a level of performance and scalability is beyond the scope of this project. </p>
			<p>We are also quite aware, through our investigation on Zeppelin, that Apache Spark does not have much built-in functionality and is actually just a bare-bones distributed computing framework. In fact, choosing to use Spark is no different from choosing to implement everything ourselves, except an added bonus of running on top of a scalable platform. </p>
			<strong>Why not R + its built-in libraries?</strong>
			<p>Our research revealed that there is actually not much difference in the functionality provided by Pandas and R + its built-in libraries. In fact, R actually has an upper hand in terms of existing functionality over Pandas, because the whole language was created for statistics and data science. </p>
			<p>However, what made us choose not to use R is because none of us are familiar with the language, so development would obviously be set back as we spend time familiarizing ourselves with the language and the libraries. </p>
			<strong>Why Pandas?</strong>
			<p>Pandas, being a data science library for Python, has a lot of built-in functionality (comparable to R) that we can use to very easily fulfill some of our basic functional requirements. However, unlike R, it has an added advantage of being a Python library, a language all of us know. </p>
			<p>Our client also requested that we use Pandas because their machine learning platform uses Pandas and Python as feature extraction pipelines, and it would be ideal if our solution was compatible with Seldon's platform. </p>
			<p>Finally, the fact that Pandas is a Python package makes it more suitable for use with a web backend. Python has many options for web application frameworks such as Django and Flask, and it would be more convenient for development if the web application and the data processing logic were both written in the same language. </p>
		</td>
	</tr>
</table>

<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #3</strong>
		</td>
		<td>
			Which web application framework will be used for the backend?		</td>
	</tr>
	<tr>
		<td rowspan="3">
			<strong>Options considered</strong>
		</td>
		<td>
			Django
		</td>
	</tr>
	<tr>
		<td>
			Flask
		</td>
	</tr>
	<tr>
		<td>
			non Python frameworks e.g. Express.js, Ruby on Rails
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			Flask
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not a non Python framework?</strong>
			<p>As we have chosen to use Pandas as a data processing library, which is a Python package, it does not make sense to use a non Python based web development framework. </p>
			<strong>Why not Django?</strong>
			<p>Django is actually better than Flask in some ways, as it is a complete framework that enforces and encourages proper code structure with the MVC paradigm and provides many features that Flask does not, such as an object-oriented wrapper over databases and built-in administration tools. However, none of this additional functionality will be necessary for our backend, making Django a bloated framework that gets in the way of performance in the context of our project. </p>
			<strong>Why Flask?</strong>
			<p>In contrast to the feature-completeness of Django, Flask advertises itself as a micro web application framework, only providing bare essentials such as routing. This makes Flask extremely lightweight and since our backend only needs the functionality Flask already provides, it is the perfect choice.  </p>
		</td>
	</tr>
</table>

<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #4</strong>
		</td>
		<td>
			Which Web framework will be used for the frontend?</td>
	</tr>
	<tr>
		<td rowspan="4">
			<strong>Options considered</strong>
		</td>
		<td>
			Angular.js
		</td>
	</tr>
	<tr>
		<td>
			Backbone.js
		</td>
	</tr>
	<tr>
		<td>
			Ember.js
		</td>
	</tr>
	<tr>
		<td>
			React.js
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			Angular.js
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not Backbone.js?</strong>
			<p>Backbone.js does not compare to Ember.js or Angular.js in terms of functionality. For example, it lacks routing, dynamic data binding and a build int templating engine. Its popularity has dwindled since its release due to the growth in popularity of more feature-filled frameworks such as Angular.js and Ember.js. </p>
			<strong>Why not React.js?</strong>
			<p>React.js is a new library that is gaining popularity among developers, but it is not a complete MVC framework like Angular.js or Ember.js, only providing the V/'view' aspect of the paradigm. Therefore, using React.js would require us spend additional time defining the MVC structure ourselves, or end up with a poorly structured app. </p>
			<strong>Why Angular.js over Ember.js?</strong>
			<p>Ember.js, along with Angular.js, were the only suitable choices for a front-end framework for our project. They are nearly identicla with regard to feature-set, but what made us choose Angular.js over Ember.js is that some of us have had experience using the former, so choosing Angular.js should streamline the development process. Furthermore, Angular.js is the more popular framework between the two and has a much larger user base in the developer community, meaning that it would be easier for us to get support if we run into problems. </p>
		</td>
	</tr>
</table>

<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #5</strong>
		</td>
		<td>
			How will the notebook interface be created?
			</td>
	</tr>
	<tr>
		<td rowspan="2">
			<strong>Options considered</strong>
		</td>
		<td>
			Jupyter + iPython kernel
		</td>
	</tr>
	<tr>
		<td>
			a custom implementation
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			Jupyter + iPython kernel
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not a custom implementation?</strong>
			<p>It would be a waste of time re-inventing the wheel when there are readily available open-source libraries that we can integrate into our project. Too much development time will be wasted dealing with the complexity of implementing a secure and robust Python execution engine as well as communication protocol.  </p>
			<strong>Why Jupyter + iPython?</strong>
			<p>Jupyter + iPython kernel is the de-facto standard notebook software for Python. It is fair to say that there are no competing solutions worth considering, and the fact that it is also included in Seldon's machine learning platform makes it a great choice. </p>
		</td>
	</tr>
</table>

<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #6</strong>
		</td>
		<td>
			How will the backend expose functionality to the frontend?
			</td>
	</tr>
	<tr>
		<td rowspan="2">
			<strong>Options considered</strong>
		</td>
		<td>
			RESTful HTTP API
		</td>
	</tr>
	<tr>
		<td>
			WebSocket API
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			WebSocket API
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not a RESTful HTTP API?</strong>
			<p>This was a tough decision to make as the REST architecture has become so prevalent among Web services that it is the de facto standard.  Providing a RESTful service would make it easy for advanced users and developers to create their own custom frontends to communicate with our backend. </p>
			<p>However, one of the architectural constraints of REST is that the web service does not store the state of the client, and the nature of our project forces us to break that constraint. For our backend to be efficient, it must store the i.e. data of the client between requests, instead of forcing the client to comply with the stateless constraint and send its data with every request. d </p>
			<p>A RESTful API is also based around HTTP, and HTTP does not allow servers to push data to clients. Our architecture must handle the situation where a client requests a data processing job that takes a long period of time, and it does not make sense to use a RESTful API, as requests will hang and might even timeout before the backend completes the data processing task. </p>
			<strong>Why a WebSocket API</strong>
			<p>Our previous assessment concluded that we ultimately need a protocol that supports pushing of updates to the client and does not enforce the constraint of statelessness, which is an inappropriate constraint for our application. </p>
			<p>Server push will most likely be a critical capability to enable synchronization of changes made using the notebook interface to the graphical/spreadsheet interface. It would also be required for the live collaboration functionality, although that is a "would have" requirement. </p>
			<p>A WebSocket API would fulfill all these requirements. </p>
		</td>
	</tr>
</table>

<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #7</strong>
		</td>
		<td>
			Which WebSocket library will be used in the front end and backend?
		</td>
	</tr>
	<tr>
		<td rowspan="2">
			<strong>Options considered</strong>
		</td>
		<td>
			none/a custom implementation
		</td>
	</tr>
	<tr>
		<td>
			Socket.IO
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			Socket.IO
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not none/a custom implementation?</strong>
			<p>It would be a waste of time re-inventing the wheel when there are readily available open-source libraries that we can integrate into our project. </p>
			<strong>Why Socket.IO?</strong>
			<p>SocketIO seems to be the only WebSocket library that has an implementation for Flask, our backend. Team members have prior experience using SocketIO. Lastly, SocketIO is backwards compatible with browsers that don't support the WebSocket protocol introduced in HTML5, so using it as a library also adds a layer of robustness and usability to our application. </p>
		</td>
	</tr>
</table>

<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #7</strong>
		</td>
		<td>
			How will the backend perform data operations?
		</td>
	</tr>
	<tr>
		<td rowspan="2">
			<strong>Options considered</strong>
		</td>
		<td>
			synchronously within Flask
		</td>
	</tr>
	<tr>
		<td>
			asynchronously outside Flask
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			asynchronously outside Flask
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not synchronously within Flask?</strong>
			<p>Although this option would make for a simpler architecture, it is definitely not good practice for the web app to be directly calling intensive data cleaning functions. It is also an approach that does not scale and performs poorly when the backend is under heavy load. Even in a production setting when Flask is deployed with a WSGI server with multiple server processes, a single blocking data processing operation would render an entire worker process unresponsive, and if enough users cause this scenario, the entire backend would become unresponsive. </p>
			<strong>Why asynchronously outside Flask?</strong>
			<p>This approach will provide scalability + robustness in the end product, overcoming the shortcomings of running the tasks synchronously within Flask. It should also boost performance as multiple cores and even multiple CPUs can be utilized to perform tasks concurrently. </p>
			<p>Running the tasks outside Flask asynchronously also enables the infrastructure to support features such as canceling operations before they complete. </p>
		</td>
	</tr>
</table>

<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #8</strong>
		</td>
		<td>
			How will backend operations be performed asynchronously?
		</td>
	</tr>
	<tr>
		<td rowspan="3">
			<strong>Options considered</strong>
		</td>
		<td>
			threading/multiprocessing within Flask
		</td>
	</tr>
	<tr>
		<td>
			service process outside Flask
		</td>
	</tr>
	<tr>
		<td>
			Celery (background task queue manager)
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			Celery (background task queue manager)
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not threading/multiprocessing within Flask?</strong>
			<p>Although this looked promising initially, testing with Flask revealed that a web app which spawns new child processes and/or uses multiple threads does not work behind a server due to restrictions in WSGI. The application only behaves as expected when run in development mode as a single threaded single process server, but not when behind any WSGI server such as Gunicorn. The idea of using multiple threads or spawning child processes within a Flask app is strongly discouraged by the developer community. Furthermore the Socket.IO library we have chosen to use with Flask does not support multithreaded web apps. </p>
			<strong>Why not a service process outside Flask?</strong>
			<p>This approach does adhere to best practices unlike using multithreading/multiprocessing, but is quite complicated to implement. With this approach, Flask would spawn a new service that performs all the data processing with every user that connects to the backend, and then communicate with that service using some form of IPC in the server OS such as a socket. There are libraries that could help with messaging such as ZeroMQ, but this approach does not compare to the simplicity of using an existing task manager solution i.e. Celery. </p>
			<strong>Why Celery?</strong>
			<p>After looking through developer forums, we saw that Celery is consistently the recommended solution for asynchronous background tasks in Python. Celery handles all aspects of background tasks, such as creating, managing and communicating with worker processes. </p>
			<p>Using Celery would allow us to queue all data processing tasks and not worry about the implementation of asynchronous background tasks. Its task management features will also simplify the development of features such as cancelling operations. </p>
		</td>
	</tr>
</table>

<table class="dialog">
	<tr>
		<td style="width:150px">
			<strong>Issue #9</strong>
		</td>
		<td>
			How will persistence of user data during sessions be achieved?
		</td>
	</tr>
	<tr>
		<td rowspan="2">
			<strong>Options considered</strong>
		</td>
		<td>
			disk cache (HDF files)
		</td>
	</tr>
	<tr>
		<td>
			in Flask web app memory
		</td>
	</tr>
	<tr>
		<td>
			<strong>Final Decision</strong>
		</td>
		<td>
			disk cache (HDF files)
		</td>
	</tr>
	<tr>
		<td>
			<strong>Rationale</strong>
		</td>
		<td>
			<strong>Why not in Flask web app memory?</strong>
			<p>In a production environment, the Flask web app will be served by a WSGI server that uses multiple different server worker processes. That means it is not guaranteed that the user’s frontend gets served by the same server process. Every server process has an independent memory stack, so storing the user data in the memory of the Flask web app as some sort of global variable, would not be a working solution. </p>
			<strong>Why disk cache (HDF files)?</strong>
			<p>The only other option is to cache the user's data on disk in a HDF file format (our research revealed that the HDF file format provides the fastest read and write speeds with Pandas data objects).  </p>
		</td>
    </tr>
</table>

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="first-iteration"></a>

## First Iteration

The user interacts with an Angular.js front-end whose HTML and other assets are served by the Flask web app. The front-end provides both spreadsheet/graphical and notebook style interfaces.

When the user launches the web app, Socket.IO (also running on Flask) establishes a two-way WebSocket connection between the Angular.js application and the Flask backend. Interactions with the spreadsheet/graphical style interface will be communicated as data retrievel, processing or cleaning requests that will be defined in our WebSocket API. When the backend receives these requests, it asynchronously launches background tasks using Celery. These background tasks will load the server's model of the user data, stored as a cached HDF file on disk, and then run functions from the standalone data cleaning Python package that we will develop on top of Pandas. Once the Celery tasks complete and return results, the backend pushes the results of the operation to the frontend over the WebSocket connection. Angular.js then updates the view in the front-end accordingly.

<div class="imgCapContainer">
    <img src="{{site.baseurl}}/assets/dev/architecture1.png" alt="Cleaning Tab"
     class="titleImage">
    <br>
    Outline of the first iteration of our application architecture.
</div>

Interactions with the notebook style interface, however, does not follow this process. The Angular.js frontend will simply display what is being served by the Jupyter notebook server running alongside Flask in the backend. Socket.IO is not used as Jupyter handles all communication of user interactions under the hood, sending the user’s Python code snippets to the iPython kernel and receiving the results of the code evaluation. The Jupyter notebook server in the backend does not connect to any iPython kernel, but rather to an iPython kernel instance that our Flask application initializes and configured to have our standalone data cleaning package imported and the server model of the user’s data retrieved and loaded from the HDF file store.

### Testing

To ensure that the architecture was designed well, we created a skeleton with all the components in place for testing. We discovered that the design of the architecture was solid except for one issue, the lack of support for asynchronous callbacks in Flask. We assumed that Flask would be queue tasks in Celery and pass in functions to be called back when the tasks complete – a common software pattern in frameworks such as Node.js. However, we realized that Celery runs functions in a separate process altogether ant is unable to call functions inside Flask. Furthermore, our research showed that Flask and most Python applications do not have an event loop and thus cannot support asynchronous callbacks. In the end, we were able to simulate asynchronous behavior by adding Celery, but instead of calling a function in Flask, the task submits a web request to an endpoint with the results data to the Flask app.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="alterations"></a>

## Alterations During Development

<div class="imgCapContainer">
    <img src="{{site.baseurl}}/assets/dev/architecture2.svg" alt="architecture"
     class="titleImage">
    <br>
    Outline of the final version of our application architecture.
</div>

The architecture of the system has undergone some changes during the development of the system. The most notable change was the withdrawal of the requirement that the system should provide *both* a pure GUI interface and a notebook style interface for performing operations on datasets. This was because our client felt that the UI of the system is good enough that a notebook style interface would not add much to the user experience of the system. To reflect this change of the system, the parts around the notebook style interface including the iPython notebook and the iPython kernel and web server. A more detailed description of the final architecture design can be found in our [technical documentation]({{site.baseurl}}/dev/architecture.html).

<br><a class="btn-resp" href="#top">^ Back to Top</a>
