# MRA
_MRA_ (_Mars Rover API_) is an API to move a rover (i.e., a planet exploration vehicle) and keeps track of its position and direction, together with the obstacles it has encountered (if any) while taking a tour on a planet.

The planet, where the rover moves, is represented as a grid with _x_ and _y_ coordinates. The planet may contain obstacles in its cells.

The rover starts its journey from the landing position -- i.e., at coordinates _(0,0)_ -- facing North.

To let the rover move on the planet, the rover receives a command string -- it can contain a single command or a combination of single commands. Once the rover has executed the commands (specified in the command string), it returns a string containing its new position and direction, together with the obstacles it has encountered (if any).

You do not need to know more so far. The _User Stories_ section will provide further details.

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

```python
# Create two obstacles at the coordinates (5,5) and (7,8).
planet_obstacles = ["(5,5)", "(7,8)"]
# Initialize the rover at the coordinates (0,0), facing North, on a 10x12 planet with obstacles at the coordinates (5,5) and (7,8)
mars_rover = MarsRover(10, 12, planet_obstacles)
# Determinate whether, or not, the planet contains an obstacle in a cell contain_obstacle = mars_rover.planet_contains_obstacle_at(7, 8)
# Specify a command string
command_string = "f"
# Let the rover move on the planet according to the command string. The return string contains the new position of the rover, its direction, and the obstacles it has encountered while moving on the planet (if any)
return_string = mars_rover.execute_command(command_string)
```

See the provided source files to improve your understanding of the API before starting to implement the user stories. 

## User Stories
Remember to read and implement the user stories once at a time (in the provided order). Therefore, do not read the next user story, if the current one is not implemented yet.

### User Story 1 -- 
The planet, where the rover moves, is represented as a grid with _x_ and _y_ coordinates. The origin of the grid, namely _(0,0)_, is at the bottom-left corner (see the figure below).


