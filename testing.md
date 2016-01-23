---
layout: default
title: Testing | ETL for Data Science
---

# Testing

To ensure that our product meets quality standards, we will be placing a heavy emphasis on software testing throughout development. This page details the testing strategies for this project.

## Unit Testing

Unit testing will be used to ensure that components within the backend and front-end are functioning properly. They will be automatically run whenever changes are made to the source code to ensure the changes did not break existing functionality. 

### Angular.js front-end

Angular.js documentation recommends the use of the Jasmine behavior driven development framework as well as the Karma command line tool to run the tests written in Jasmine to run on different browsers. We will be following this recommendation. 

### Flask back-end

The Flask web application framework supports unit testing by simulating HTTP clients. Unit tests can then be written in any Python testing framework of our choice, and the Flask documentation shows examples using the testing module built into Python called unittest. However, we will be using a popular alternative to the default testing module, called py.test. The advantage of using py.test is that it does not require the developer to write any boilerplate (repetitive) code thus saving time.  

### Python data cleaning package

Unit tests for the Python data cleaning package will also be written using py.test. 

## Integration & Functional Testing

Integration testing will be used to ensure that the back-end and front-end components are functioning properly as an interconnected system. Functional testing will be used to ensure that the functional requirements of the product have been fulfilled. They will both be accomplished in this project by performing end to end testing on the Angular.js front-end. 

Selenium is an open-source testing framework that is frequently used for testing web applications but we will be using Protractor, the end to end testing framework recommended by the Angular.js documentation. Protractor is specifically designed for testing Angular.js applications and actually uses the server component of the Selenium framework. Protractor simulates the user’s interactions with the user interface across all major browsers and tests the behavior of the application. Protractor tests uses the same syntax as Jasmine, our choice of unit testing framework for Angular.js, so it should make writing test code more convenient. 

## User Acceptance Testing (UAT)

To ensure that our clients are satisfied with our product will be conducting UAT on a regular basis with our clients at Seldon. We aim to begin regularly incorporating UAT into our weekly Scrum sprints when we have completed the user interface in the front-end, and interaction with the system becomes possible. The UAT will be thoroughly planned in advance of the meetings, with test scenarios written in a format similar to use cases. We will only consider new features we develop to be completed the our clients have accepted them in the user acceptance tests. There is a chance we may reduce the frequency of UAT to every two weeks, if we see that not enough progress can be made to show for in a weekly sprint. 

<br><a class="btn-resp" href="#top">^ Back to Top</a>