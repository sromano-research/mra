# MRA
_MRA_ (_Mars Rover API_) is an API to move a rover (i.e., a planet exploration vehicle) and keeps track of its position and direction, together with the obstacles it has encountered (if any) while taking a tour on a planet.

The planet, where the rover moves, is represented as a grid with x and y coordinates. The planet may contain obstacles in its cells.

The rover starts its journey from the landing position -- i.e., at coordinates _(0,0)_ -- facing North.

To let the rover move on the planet, the rover receives a command string -- it can contain a single command or a combination of single commands. Once the rover has executed the commands (specified in the command string), it returns a string containing its new position and direction, together with the obstacles it has encountered (if any).

You do not need to know more so far. The User Stories section will provide further details.

## Instructions for You
* FORK this project and make sure your forked repository is PUBLIC. Then, IMPORT the forked project into PyCharm.
* If you BELONG to the GAI4-TDD group, you are asked to develop _MRA_ by following **TDD WITH** the support of **GAI4-TDD**. If you do NOT BELONG to the GAI4-TDD group, you are asked to develop _MRA_ by following **TDD WITHOUT** the support of **GAI4-TDD**.
* You DO NOT need to develop a GUI.
* You CANNOT change the signature of the provided methods, move the provided methods to other classes, or change the name of the provided classes. However, you CAN add fields, methods (e.g., methods called by the provided methods), or even classes (including other test classes), as long as you comply with the provided API.
* You CAN use the internet to consult Python APIs or QA sites (e.g., StackOverflow).
* You CANNOT use AI tools (if you are in the GAI4-TDD group, you can use GAI4-TDD of course).
* You CANNOT interact with your colleagues. Work alone and do your best!
* The _MRA_ requirements are divided into a set of USER STORIES, which serve as a to-do list (see the _User Stories_ section).
* You should be able to incrementally develop _MRA_ without an upfront comprehension of all its requirements. DO NOT read ahead and handle the requirements (specified in the user stories) one at a time in the provided order. Develop _MRA_ by starting from the first story's requirement. When a story is IMPLEMENTED, move on to the NEXT one. A story is implemented when you are confident that your program correctly implements the functionality stipulated by the story's requirement. This implies that all your test cases for that story and all the test cases for the previous stories pass. You may need to review your program as you progress toward more advanced requirements.
* Each time you end a GREEN or REFACTOR phase, COMMIT.
* At the end of the task, PUSH your forked project.

## API Usage
Take some minutes to understand, in broad terms, how the API works. If you do not fully understand the API, do not worry because more details will be given later in the _User Stories_ section. A typical API usage follows.

