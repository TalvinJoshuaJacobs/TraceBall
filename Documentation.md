**West Herts College - *HND in Computing (Cyber Security)* ->  *Programming - Assignment 1*** By Talvin Jacobs (2018-2019)

## 'TraceBall'

### I. Initiative
Set inside a browser window, the user controls a small box connected to the mouse and has to escape (not have his box touched by) an enemy box controlled by an AI. The user has three lives (a life is lost once the enemy box touches the users box) and their objective is to last as long as they can.

### II. Epics and User Stories

##### Epics

 - The game is coded in Javascript and HTML and on Notepad only
 - The user has to control his box by using the mouse only
 - The enemy is controlled by an AI which uses math functions (trigonometry) to work out the player's position
 - The game takes place inside a canvas 
 - The user has three lives. They lose a life if the enemy box touches the user's box. If they lose all of their lives,       the user loses the game


##### Non-Functional Requirements

 - The user controls a green box 
 - The enemy AI controls a red box
 - The boxes are of the same size
 - The speed of the enemy AI is balanced (so the game isn't too difficult, but also not too easy)
 - The number of lives is displayed below the canvas
 - The title of the game is displayed above the canvas in a clear, bold font

##### User Stories

"As a player,  I would like the enemy AI to follow my box more smoothly, for a better and more enjoyable gaming experience."
"It would be nice for the canvas to appear in the middle of the page, where my eyes would normally rest."
"As a player, I would love to see how many lives I have left during gameplay."


##### How We Addressed The Requirements

My game has had a life-score and a smoother AI implemented, as well as a nicer, more pleasant looking canvas.
The life-score function and the smoother AI were both implemented with the help of a fellow student (Eric Vasile). The canvas was completed by myself.

### III. Genre
Simple 2D browser game

### IV. Technical Details

##### Platform
HTML Browser platform

##### Programming Language/Enviroment
Javascript and HTML

##### Programming Challenges
I had to overcome numerous challenges:

 - Not having any previous experience or knowledge with Javascript
 - Working with Notepad (Default windows text editor application, which isn't a feature-rich IDE)
 - Having to code the Enemy AI (working out which way was best to code it)
 - Making the game appear more tidy (visually)
 - Implementing the '3 lives' rule 
 - Coding the crash rule (Making sure the game stops and a life is lost when the user's box touches the enemy box)

##### Constructing And Implementing My Code

To begin, I went to https://www.w3schools.com/graphics/game_intro.asp and learned the basics of Javascript and how it functions. I then looked at the example game and learnt what each part of the code was responsible for (By going through the code, deleting some lines, and comparing it with the full final result).
Then, I navigated to the sections of the website which highlighted the different functions of the game and wrote my code with that as a reference.
Each 'chunk' of my code was written by referring to different parts of the w3schools website.
I then hit a brick wall. I wasn't able to code the 'Enemy AI' to get it to chase the user's box. I spent a few days trying to figure out how to code it, and ended up referring to a classmate's (Eric Vasile) piece of code to get it completed.

##### Algorithms

The algorithm found in my code is responsible for the Enemy AI, getting it to chase the user's box in the most efficient way possible. This was done by getting the Enemy to do 2 things: 1) Calculate the shortest distance between it and the user, and 2) Follow that path linearly, at a constant speed. To get it to calculate this 'shortest distance', I've implemented Pythagoras' theorem using the Math function and the coordinates of the user's mouse. 
 
##### Coding Standards 
I've stuck to the following when writing the code:

 - The variable names and cases are consistent
 - The spacing, indentation, comments and brackets are consistent
 - The code is readable

I've stuck to placing the opening bracket on the same line as the object name, and also made sure each line generally wasn't longer than 100 characters.
The format of the code on GitHub will look slightly different to when it is pasted in Notepad or an appropriate IDE - The indentation will appear inconsistent, however this doesn't change the structure or affect the functionality of the code.

I have not used camelCase, but instead, stuck to Capitalized variable names. They are all consistent with this case.

### V. Research
I used https://www.w3schools.com for my research before completing this task.

### VI. Project Management

##### Burndown Chart

![My Burndown Chart](http://i.imgur.com/wQpg17yg.jpg)

This chart shows the completion of each individual 'chunk' of code over time. (This chart shows that I was slightly ahead of schedule for the majority of the task)

##### User Stories Tracking Chart (Which Stories Have Been Completed)

![enter image description here](https://i.imgur.com/kEawMv3.jpg)
##### Flowchart

![My flowchart](http://i.imgur.com/cT43un3.jpg)

##### Functions

 - "Get the player to control the box using the mouse":  Using `this.canvas.addEventListener('mousemove', function (e) {` , the player's mouse movement is recorded and the player's box element is placed exactly where the cursor is.
 - "The user has 3 lives":  This is a rule that is implemented as a functional requirement.
 - "Get the co-ordinates of the player's mouse for each frame": The user's cursor position will be constantly moving to a different position on the canvas. This needs to be tracked, for use of the enemy AI.
 - "Calculate the shortest distance between the enemy box and the player's mouse co-ordinates": The shortest "line" between two points can be calculated by using Pythagoras' theorem (a^2 + b^2 = c^2). This is the invisible line that the enemy will always traverse when chasing the player. (It's the most efficient way for the enemy to do so).
 - "Continue until the player DOES touch the enemy": If the enemy's box hasn't yet touched the player's box, the game can still continue until it happens. It must happen as the game cannot go on forever! (Humans don't live forever)
 - "Deduct 1 life": This occurs when the player has touched the enemy box, AND has more than 1 life left. 
 - "Pause for 450 milliseconds": This is to give the player a little break and to clarify that the next "round" will begin after the pause.  `setTimeout(updateGame,450);`
 
##### Flowchart -> Code

> "Display the player's box, the enemy's box and the canvas"

    var GameArea = { 						//Displays Canvas
	    canvas : document.createElement("canvas"),
	    start : function() {
		    var TheCanvas = document.getElementById("Space");
		    this.canvas.width = TheCanvas.width;
		    this.canvas.height = TheCanvas.height;
		    this.canvas.style = "border:20px solid #000000";
		    this.canvas.style = "background-color: #D5D5D5";
		    this.context = this.canvas.getContext("2d");
		    TheCanvas.parentNode.replaceChild(this.canvas, TheCanvas);
		    window.requestAnimationFrame(updateGame);
		    
    var Gamer;							//Created the Player
    var Enemy;							//Created the Enemy
    
    function Start() {
    GameArea.start();
	    Gamer = new Entity(70, 70, "#55822B", 1000, 500);		//Player's attributes
	    Enemy = new Entity(70, 70, " #C70039", 240, 115);		//Enemy's attributes
    }

> Get the player to control the box using mouse

    this.canvas.style.cursor = "none"; 				//Hides the mouse
    this.canvas.addEventListener('mousemove', function (e) { 	//Getting mouse movement
	    GameArea.plrX = e.offsetX;
	    GameArea.plrY = e.offsetY;
	    })
    },

> The user has 3 lives

    var PlayerLives = 4;						//Starting number
    var Lives = document.getElementById("Lives");
    
    function updateGame() {
	    if (Enemy.crashWith(Gamer)) {
		    window.cancelAnimationFrame(ThisFrame);
		    PlayerLives += -1; 					//Player loses life if crash = true
		    if (PlayerLives <= 0) {
			    Lives.innerHTML = "Game Over :(";
		    }
		    else {
			    Lives.innerHTML = PlayerLives + " lives remaining"; //Displays the number of lives on the page
			    Restart();
		    }

> Get the co-ordinates of the player's mouse for each frame 

    function Restart() {
	    GameArea.clear();
	    Gamer.x = 1000;
	    Gamer.y = 500;
    }


    function Entity(width, height, color, x, y) {
	    this.width = width;
	    this.height = height;
	    this.x = x;
	    this.y = y;
	    this.update = function() {
		    ctx = GameArea.context;
		    ctx.fillStyle = color;
		    ctx.fillRect(this.x, this.y, this.width, this.height);
		    this.relX = this.width/2+this.x;
		    this.relY = this.height/2+this.y;
	    }
    }

> Calculate the shortest distance between the enemy box and the player's mouse co-ordinates

    function GetNewCoords(startObj,destinationObj,ThisFrame) {
	    var dx = destinationObj.relX - startObj.relX;
	    var dy = destinationObj.relY - startObj.relY;
	    var Distance = Math.sqrt(dx * dx + dy * dy);
	    if (Distance) {
		    dx /= Distance;
		    dy /= Distance;
	    }

> Get the enemy box to traverse this "shortest distance"
	  
    Hypotenuse = ThisFrame - EndFrame;
    EndFrame = ThisFrame;
    var x = dx * Hypotenuse * 6.85;
    var y = dy * Hypotenuse * 6.85;
    return {x,y};
    }
> 
> Pause for 450 milliseconds

	    Gamer.update();
	    Enemy.update();
	    setTimeout(updateGame,450);
    }

