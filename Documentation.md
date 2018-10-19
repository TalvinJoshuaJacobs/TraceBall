## 'TraceBall'

### I. Initiative
Set inside a browser window, the user controls a small box connected to the mouse and has to escape (not have his box touched by) an enemy box controlled by an AI. The user has three lives (a life is lost once the enemy box touches the users box) and their objective is to last as long as they can.

### II. Epics and User Stories

##### Epics

 - The game is coded in Javascript and HTML and on Notepad only
 - The user has to control his box by using the mouse only
 - The enemy is controlled by an AI which uses math functions (trigonometry) to work out the player's position
 - The game takes place inside a canvas 
 - The user has three lives. They lose a life if the enemy box touches the user's box. If they lose all of their lives, the user loses the game


##### Non-Functional Requirements

 - The user controls a green box 
 - The enemy AI controls a red box
 - The boxes are of the same size
 - The speed of the enemy AI is balanced (so the game is not too difficult, but also not too easy)
 - The number of lives is displayed below the canvas
 - The title of the game is displayed above the canvas in a clear, bold font

##### User Stories

 - "As a player, I want to clearly see the game area, my box and the enemy box."
 - "As a player, I want my mouse to be hidden when playing."
 - "As a player, I would like the game to stop and restart when I come into contact with the enemy."
 - "As a player, I will need to see the enemy follow my box in the most efficient (and balanced) way possible."
 - "As a player, I would like the enemy AI to follow my box more smoothly, for a more enjoyable gaming experience." 
 - "It would be nice for the canvas to appear in the middle of the page, where my eyes would normally rest."
 - "It would be great to have a score function which goes up as time goes by while being alive."
 -  "As a player, I would love to see how many lives I have left during game-play."


##### How We Addressed The Requirements

A plan was devised so that all the functional requirements would be completed with the highest priority, followed by the non-functional requirements.

### III. Genre
Simple 2D browser game

### IV. Technical Details

##### Platform
This project was coded entirely in Notepad (the default text application that comes with windows). This means I did not use an IDE for the program.

##### Programming Language/Enviroment
Javascript and HTML

##### Programming Challenges
Numerous challenges had to be overcome:

 - Not having any previous experience or knowledge with Javascript
 - Working with Notepad (Default windows text writing application, which is not a feature-rich IDE)
 - Having to code the Enemy AI (working out which way was best to code it)
 - Making the game appear more tidy (visually)
 - Implementing the '3 lives' rule 
 - Coding the crash rule (Making sure the game stops and a life is lost when the user's box touches the enemy box)

##### Construction and Implementation of the Code

To begin with, https://www.w3schools.com/graphics/game_intro.asp was visited and the basics of Javascript and how it functions were learnt. The example game was studied for what each part of the code was responsible for (By going through the code, deleting some lines, and comparing it with the full final result).
Then, different sections of the website which highlighted the different functions of the game were visited and the code was written with that as a reference.
Each 'chunk' of the code was written by referring to different parts of the w3schools website.
Then an issue arised. Attempting to code the 'Enemy AI' was a huge struggle, as well as getting it to chase the user's box. A few days were spent trying to figure out how to code it, but eventually a classmate's (Eric Vasile) piece of code was referred to to get it completed.

##### Algorithms

An algorithm in the code is responsible for the Enemy AI, getting it to chase the user's box in the most efficient way possible. This was done by getting the Enemy to do 2 things: 1) Calculate the shortest distance between it and the user, and 2) Follow that path linearly, at a constant speed. To get it to calculate this 'shortest distance', Pythagoras' theorem was implemented using mathematical functions and the coordinates of the user's mouse. 

Another algorithm is responsible for the life system. Since the player only has 3 lives, it is essential that this is done properly, as it is the central part of the game. First, a variable needed to be created for the number of lives the player has. Then, the rule that 'if the enemy box touches the user's box, a life is deducted' was implemented. There will always be a point in time when the enemy box does touch the user's box, so after that, a life will be deducted ONLY IF the user has more than one life remaining, otherwise, the game is over.
 
##### Coding Standards 
The following coding standards were adhered to when completing the code:

 - The variable names and cases are consistent
 - The spacing, indentation, comments and brackets are consistent
 - The code is readable

The opening brackets remain on the same line as the object name, and also each line generally is not longer than 100 characters (except for the comments).
The format of the code on GitHub will look slightly different to when it is pasted in Notepad or an appropriate IDE - The indentation will appear inconsistent, however this does not change the structure or affect the functionality of the code.

camelCase was not used, but instead Capitalized variable names were. They are all consistent with this case.

### V. Research
https://www.w3schools.com was used as a source before completing this task.

### VI. Project Management

##### Burndown Chart

![Burndown Chart](http://i.imgur.com/wQpg17yg.jpg)



##### User Stories Tracking Chart (Which Stories Have Been Completed)

![enter image description here](https://i.imgur.com/kEawMv3.jpg)
##### Flowchart

![My flowchart](https://i.imgur.com/o2Pzegi.jpg)

##### Functions

 - "Get the player to control the box using the mouse":  Using `this.canvas.addEventListener('mousemove', function (e) {` , the player's mouse movement is recorded and the player's box element is placed exactly where the cursor is.
 - "The user has 3 lives":  This is a rule that is implemented as a functional requirement.
 - "Get the co-ordinates of the player's mouse for each frame": The user's cursor position will be constantly moving to a different position on the canvas. This needs to be tracked, for use of the enemy AI.
 - "Calculate the shortest distance between the enemy box and the player's mouse co-ordinates": The shortest "line" between two points can be calculated by using Pythagoras' theorem (a^2 + b^2 = c^2). This is the invisible line that the enemy will always traverse when chasing the player. (It is the most efficient way for the enemy to do so).
 - "Continue until the player DOES touch the enemy": If the enemy's box has not yet touched the player's box, the game can still continue until it happens. It must happen as the game cannot go on forever! (Humans do not live forever)
 - "Deduct 1 life": This occurs when the player has touched the enemy box, AND has more than 1 life left. 
 - "Pause for 450 milliseconds": This is to give the player a little break and to clarify that the next "round" will begin after the pause.  `setTimeout(updateGame,450);`
 
##### Flowchart -> Code

> "Display the player's box, the enemy's box and the canvas":

    var Gamer; // The player
    var Enemy; // The enemy
    
    function Start() { // 2 entities are created when the game begins:
	    GameArea.start();
	    Gamer = new Entity(70, 70, "#55822B", 1000, 500); // The player's box and its characteristics
	    Enemy = new Entity(70, 70, " #C70039", 240, 115); // The enemy's box and its (similar) characteristics
    }

    // The setting up of the Canvas (Area where the game takes place - The "Map")
    var GameArea = { // It is set up as a new variable
	    canvas : document.createElement("canvas"), // The canvas element is created
	    start : function() {
		    var TheCanvas = document.getElementById("Space"); // Another DOM grabber
		    this.canvas.width = TheCanvas.width;
		    this.canvas.height = TheCanvas.height;
		    this.canvas.style = "border: 20px solid #000000"; // Canvas style and size
		    this.canvas.style = "background-color: #D5D5D5"; // ^
		    this.context = this.canvas.getContext("2d");
		    TheCanvas.parentNode.replaceChild(this.canvas, TheCanvas); // Overwriting the canvas info
		    window.requestAnimationFrame(updateGame); // Creates the animation in Javascript
    },

> "Get the player to control the box using mouse":

    this.canvas.style.cursor = "none"; // Hides the mouse cursor

    this.canvas.addEventListener('mousemove', function (e) { // Gets the program to listen out for the mouse co-ordinates
	    GameArea.plrX = e.offsetX; // Mouse's x co-ordinates
	    GameArea.plrY = e.offsetY; // Mouse's y co-ordinates
    })

> "The user has 3 lives" (And what happens to the player if a life is lost):

    var PlayerLives = 4; // Number of Lives the player begins with
    var Lives = document.getElementById("Lives"); // A Document Object Model (DOM) grabber
    
    function updateGame() {
	    if (Enemy.crashWith(Gamer)) { // Telling the program what happens when a 'crash' DOES occurs
		    window.cancelAnimationFrame(ThisFrame);
		    PlayerLives += -1; // A life is deducted as a result of a crash
		    if (PlayerLives == 0) { // However, if the player lands with 0 lives after crashing...
			    Lives.innerHTML = "Game Over :("; // ... It is game over for the player
		    }
		    else {
			    Lives.innerHTML = PlayerLives + " lives remaining"; // Displays the number of lives remaining on screen
			    Restart(); // The game is restarted if the player does have a sufficient number of lives left
	    }
    }

> "Get the co-ordinates of the player's mouse for each frame":

    this.canvas.addEventListener('mousemove', function (e) { // Gets the program to listen out for the mouse co-ordinates
	    GameArea.plrX = e.offsetX; // Mouse's x co-ordinates
	    GameArea.plrY = e.offsetY; // Mouse's y co-ordinates
    })

    function GetNewCoords(startObj,destinationObj,ThisFrame) {
	    var dx = destinationObj.relX - startObj.relX; // The x (width) of the hypotenuse
	    var dy = destinationObj.relY - startObj.relY; // The y (hight) of the hypotenuse
    }

> "Calculate the shortest distance between the enemy box and the player's mouse co-ordinates":

    function GetNewCoords(startObj,destinationObj,ThisFrame) {
	    var Distance = Math.sqrt(dx * dx + dy * dy); // The shortest distance between the enemy's co-ordinates and the player's co-ordinates using Pythagoras' theorem
	    if (Distance) {
	    dx /= Distance;
	    dy /= Distance;
    }

> "Get the enemy box to traverse this "shortest distance":
	  
    function GetNewCoords(startObj,destinationObj,ThisFrame) {
	    ElapsedTime = ThisFrame - EndFrame; // Time elapsed,
	    EndFrame = ThisFrame;
	    var x = dx * ElapsedTime * 7; // Multiply the separating x-distance with the time elapsed and the speed of the action (7 in this case)
	    var y = dy * ElapsedTime * 7; // Multiply the separating y-distance with the time elapsed and the speed of the action (Also 7 in this case)
	    return {x,y}; // Gets the enemy to move to the previously defined co-ordinates - This is the enemy AI in action
    }
> 
> Pause for 450 milliseconds

	    setTimeout(updateGame,450); // The time delay between the player's death and the start of the new life


