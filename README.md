## NODE2.1: Jade

#### Objective
Learn how to author HTML documents in the Jade templating language.

####Skills
* Express View Engines
* Express render()
* Jade

#### Resources
##### Documentation

* [Jade Syntax Documentation by example](http://naltatis.github.io/jade-syntax-docs/)
* [jade-lang.com](http://jade-lang.com/) official documentation, but not the best

##### Tutorials

* [Learn Jade Tour](http://www.learnjade.com/tour/intro/) (start here!)
* [A Simple Website in Node.js with Express, Jade and Stylus](http://clock.co.uk/tech-blogs/a-simple-website-in-nodejs-with-express-jade-and-stylus)
* [Ninja Store Tutorial](http://www.hacksparrow.com/express-js-tutorial.html) (thorough example)

##### Tools

* [HTML to Jade Converter](http://html2jade.aaron-powell.com/)

#### Requirements

#### Part I: Basic Express Setup

1. Create a new Projects folder.
2. Open terminal and navigate to the folder you just created so you can run commands from there.
3. Run __express__. This will create the boilerplate files for your Node app.
4. Run __npm install__. This will install all the libraries listed as dependencies in package.json (which are only express and jade to begin with).
5. Run __node app.js__ or __supervisor app.js__ to start the web server.

  __Node:__ If your server fails to start and you see the error "EADDRINUSE" it means that a program (most likely another node app) is already running on that port. You will need to kill the other server or change the port number in app.js before running your server.

6. Test that your basic express server is working by navigating to [http://localhost:3000](http://localhost:3000) in your browser.

#### Part II: A Taste of Jade

Jade is a templating language that compiles into HTML. Follow the instructions below to get your first taste of Jade. Look at the explanation at the end of Part III to learn how Jade is integrated within Express.

1. Open /views/index.jade in your text editor. Change the content of the h1 element to "I'm Jaded".
2. Refresh the site in your browser to confirm your change.
3. Add an h2 element with some text to the end of the content block in /views/index.jade.
4. Refresh the site in your browser to confirm your change.
5. Add a link to /views/index.jade:

  ```
  a(href='http://fall2013.refactoru.com') Student Site
  ```

6. Refresh the site in your browser to confirm your change. (Incremental Programming FTW!)

#### Part III: Passing Data to Views

1. Open /routes/index.js in your text editor. Change the value of the title property to "Buck Wild".
2. Restart your node server.
3. Refresh the site in your browser to confirm your change.

  __What's going on here?__ So far we have used __res.send()__ to send a response to the client. Express has another way to send a response to the client: __res.render()__.
  If __res.render()__ is used, Express will generate HTML from a given template written in HTML, ERB, Jade, or another templating language. Express is configured to use Jade as its default view engine. This can be seen in the following line in app.js:
  ```
  app.set('view engine', 'jade');
  ```

  The first argument to __res.render()__ is the name of the template. This is just the name of a jade file in the /views directory minus the .jade extension. While /views is the default directory where express looks for views, you can change this in app.js:
  ```
  app.set('views', __dirname + '/views');
  ```

  The second argument to __res.render()__ is an object containing key-value pairs that gets passed to the view and are accessible in the view via __#{propertyName}__ or __p= propertyName__ as seen in /views/index.jade.
  Using templates provides a clean separation between your HTML and the data that gets injected in it. Furthermore, Express separates the view from the routing logic by placing the views in a separate folder and letting __res.render__ act as the 'glue'. This is the basis of the MVC Pattern: separating __Model__ (your data), __View__ (presentation), and __Controller__ (handling user requests and joining the Model with the View).

#### Part IV: Diving Into Jade

Use [Jade Syntax Documentation](http://naltatis.github.io/jade-syntax-docs) by example and other resources (See __Resources__ section above) to try out different Jade commands in /views/index.jade. At minimum learn and get practice with the following language constructs  :

  * tags
  * id and class literals
  * attributes
  * piped text
  * conditionals
  * mixins
