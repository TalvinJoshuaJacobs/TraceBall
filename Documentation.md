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
"As a player,  I would love to be able to see my score displayed somewhere on the screen, to give me an incentive to continue trying to survive."
"It would be nice to have difficulty levels to chose from, so that I can play against a slower or faster AI."


##### How We Addressed The Requirements

My planned product would implement a score function and a difficulty setting.

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

### V. Research
I used https://www.w3schools.com for my research before completing this task.

### VI. Project Management

##### Burndown Chart

![My Burndown Chart](http://i.imgur.com/wQpg17yg.jpg)

This chart shows the completion of each individual 'chunk' of code over time. (This chart shows that I was slightly ahead of schedule for the majority of the task)

##### User Stories Tracking Chart (Which Stories Have Been Completed)

(I haven't been able to implement the user stories as of yet)

##### Flowchart

![My flowchart](http://i.imgur.com/cT43un3.jpg)

##### Functions

 - "Get the player to control the box using the mouse":  Using `this.canvas.addEventListener('mousemove', function (e) {` , the player's mouse movement is recorded and the player's box element is placed exactly where the cursor is.
 - "The user has 3 lives":  This is a rule that is implemented as a functional requirement.
 - "Get the co-ordinates of the player's mouse for each frame": The user's cursor position will be constantly moving to a different position on the canvas. This needs to be tracked, for use of the enemy AI.
 - "Calculate the shortest distance between the enemy box and the player's mouse co-ordinates": The shortest "line" between two points can be calculated by using Pythagoras' theorem: a^2 + b^2 = c^2. This is the invisible line that the enemy will always traverse when chasing the player. (It's the most efficient way for the enemy to do so).
 - "Continue until the player DOES touch the enemy": If the enemy's box hasn't yet touched the player's box, the game can still continue until it happens. It must happen as the game cannot go on forever! (Humans don't live forever)
 - "Deduct 1 life": This occurs when the player has touched the enemy box, AND has more than 1 life left. 
 - "Pause for 450 milliseconds": This is to give the player a little break and to clarify that the next "round" will begin after the pause.  `setTimeout(updateGame,450);`
