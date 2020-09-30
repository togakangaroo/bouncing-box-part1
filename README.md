# Bouncing Box Game: Part 1 (An amazing project)

We're going to create a simple game where a box moves across the screen at an increased speed after each click.

[When you are done it should look like this](http://jsbin.com/lutuhu/1)

Our goal for this game is to learn how to bring together HTML, CSS, and JavaScript. We use HTML to define our structure, CSS to define the style of that structure, and JavaScript in order to implement behavior. One of the primary ways we can implement behavior in JavaScript is by making modifications to the HTML and CSS in response to **events** which we will demonstrate by making this simple game. 

## Let's get started

* Visit Cloud 9
* Create an HTML5 workspace
* Click the 'Start Editing' button

## A note about jQuery

We are going to be using [jQuery](https://jquery.com) for this exercise. You can see that we've included it in our web page with the following HTML 

    <script src="//cdnjs.cloudflare.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>

jQuery is a powerful library which makes building web pages easier. It is also tremendously popular. If you are doing web development in 2015, you will likely run into jQuery. That is why we are introducing just a tiny bit of it here. 

You can recognize jQuery by its use of a very curious function `$()` Here is some of the jQuery code we use in this page:

    box = $('.box');
    boardWidth = $('.board').width();

### TODO 1: Create and Style Box

The HTML for our box has already been created for us:

    <body class="board">
      <div class="box">?</div>
    </body>

Find the CSS that styles the box and change the following properties:

- `left`
- `top` 
- `width`
- `height`

Notice how you can change the appearance of the box using CSS! Now return those to their original values

    width: 70px;
    height: 70px;
    top: 100px;
    left: 0px;

### TODO 2: Learn how to move the box

You can also change the appearance of the box using JavaScript. 

Declare and initialize `position` and `points` variables to zero

    // TODO 2
    var position;
    var points;
    var speed;

    position = 0;
    points = 0;
    speed = 10;

Now add the following code under `TODO 2`
    
    box.css('left', position);

Now change the value of the `position` variable and watch the box move

JavaScript lets us change HTML as well. Add the following JavaScript code under `TODO 2`

    box.text(points);

Change the `points` variable and watch how it changes the box. 

Before we move on, lets reset those variables to their starting values

    position = 0;  
    points = 0;  
    speed = 10;

### TODO 3: Animating the box

You can create animation on a web page by changing the appearance of an object over time. A traditional animation is made up of individual "frames" of still images. If you flip between these images rapidly and each image is just slightly different than the previous image, the viewer sees the scene as motion. We do the same thing in programming. 

The `setInterval` function allows us to setup a timer, where we call a function every so often. **How often**, the time between function calls, is called the interval. That interval is expressed in milliseconds, or thousandths of a second. 

The following code:
    
    setInterval(update, 50);

Calls our `update` function ever 50 milliseconds, which is about 20 times per second. 

To animate the box, add the following code to the update function

    update = function() {
        position = position + speed;
        box.css('left', position);
    };

This changes our position on every call to `update` and then also moves the box to that position.

### TODO 4: Hey box, come back!

Each time we call the `update` function the position variable gets larger and larger until eventually our box has gone off the screen. The position of our box should never be greater than the width of the board. Add the following code **inside** the `update` function

    if(position > boardWidth) {
        position = 0;
    }

Your `update` function should look like this:

    update = function() {
        position = position + speed;
        if(position > boardWidth) {
         position = 0;
        }
        box.css('left', position);
    };

### TODO 5: Handling events

An event is just a particular thing that has happened. Some examples of **events** are:

- A timer going off
- The user clicking on something
- the web page has finished loading

JavaScript allows us to change the web page in response to **events**. The following code calls the `handleBoxClick` function every time the box is clicked. 

    box.on('click', handleBoxClick);

Every time the user clicks the box, we want to reset the box to its starting position and make the game harder by increasing the speed of the box. Add the following code to the `handleBoxClick` function

    handleBoxClick = function() {
      speed = speed + 3;
      position = 0;
    }

### TODO 6: Keeping Score

We want to keep track of how many times the user has clicked on the box. 

Add the following code to the `handleBoxClick` function

     points = points + 1;

and then add the following code to the `update` function

    box.text(points);

What's going on here?

## Good Job

You've written your first game! Here are some ways you can try and make your game even more awesome.

### Can you move the box up and down?
### Can you change the size or color of the box with each click?
### Use the [background-image](http://www.w3schools.com/cssref/pr_background-image.asp) CSS property to change your box or the background

