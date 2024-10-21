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
* At the end of the task, PUSH your forked project and fill in the following post-questionnaire: https://forms.gle/5F1SjWfzXyikHKWBA.

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

### User Story 1 -- Planet
The planet, where the rover moves, is represented as a grid with _x_ and _y_ coordinates. The origin of the grid, namely _(0,0)_, is at the bottom-left corner (see the figure below).

The planet may contain obstacles in its cells. The obstacles are defined through a list of strings (without white spaces), where each string (representing an obstacle) is formatted as follows: _"(oi_x,oi_y)"_. For example, a list containing the strings _"(0,1)"_ and _"(2,2)"_ indicates that there are two obstacles on the planet: the former in the cell with coordinates _(0,1)_ and the latter in the cell with coordinates _(2,2)_ (see the figure below). 

![image](https://github.com/user-attachments/assets/248d5301-70fd-49e0-99df-100ae72c20f3)

**Requirement:**
* Implement ```MarsRover.__init__(self, planet_length: int, planet_width: int, planet_obstacles: list[str])``` to define a planet as a grid with a given length (x-axis) and width (y-axis) and obstacles in its cells.
* Implement ```MarsRover.planet_contains_obstacle_at(self, x: int, y: int) -> bool``` to determine whether, or not, a cell contains an obstacle.

**Example:** 
* A 10x10 planet with two obstacles at (4,7) and (2,3).

### User Story 2 -- Landing
The rover has a position (defined by _x_ and _y_ coordinates) and a direction -- i.e., where the rover is facing. The direction can be North (_N_), South (_S_), West (_W_), or East (_E_).

The rover starts its journey from the landing position -- i.e., the position with coordinates (0,0) --, facing North (see the figure below). 

![image](https://github.com/user-attachments/assets/2f8d792c-3e42-40d6-97b1-5b535faea161)

To let the rover move on the planet, the rover receives a command string. Once the rover has executed the commands (specified in the command string), it returns a string containing its new status, together with the obstacles it has encountered (if any). The rover status is a string (without white spaces) formatted as follows: _"(x,y,dir)"_. For example, _"(0,1,W)"_ indicates that the rover is in the position with coordinates _(0,1)_, facing West. It is easy to follow that _dir_ is equal to: _N_ (North), _S_ (South), _E_ (Est), or _W_ (West).

When the rover receives an empty command string, it returns a string consisting of the landing status -- i.e., the string _"(0,0,N)"_.

**Requirement:**
* Implement ```MarsRover.__init__(self, planet_length: int, planet_width: int, planet_obstacles: list[str])``` to define a planet (already done in the previous user story) and to initialize the rover to the landing position, facing North.
- Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover return a string consisting of its landing status when it receives an empty command string (i.e., _""_).
 
**Example:** When the rover receives an empty command string, it returns a string consisting of its landing status, namely: _"(0,0,N)"_.

### User Story 3 -- Turning
The rover turns right or left when it receives a command string _"r"_ or _"l"_, respectively. When the rover turns, it remains on the same grid's cell while it changes its direction.

**Requirement:** 
* Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover turn right or left and then return a string consisting of its new status.
 
**Examples:**
* A rover with status _"(0,0,N)"_, after executing the command string _"r"_, returns a string consisting of its new status, namely: _"(0,0,E)"_.
* On the other hand, a rover with status _"(0,0,N)"_, after executing the command string _"l"_, returns: "(0,0,W)".

### User Story 4 -- Moving Forward
The rover moves forward (of one cell) when it receives the command string _"f"_.
 
**Requirement:** 
* Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover move forward and then return a string consisting of its new status.
 
**Example:** 
* A rover with status _"(7,6,N)"_, after executing the command string _"f"_, returns a string consisting of its new status, namely: _"(7,7,N)"_.

### User Story 5 -- Moving Backward
The rover moves backward (of one cell) when it receives the command string _"b"_.

**Requirement:** 
* Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover move backward and then return a string consisting of its new status.

**Example:** 
* A rover with status _"(5,8,E)"_, after executing the command string _"b"_, returns a string consisting of its new status, namely:_"(4,8,E)"_.

### User Story 6 -- Moving Combined
The command string can contain a combination of single commands (i.e., _"r"_, _"l"_, _"b"_, and _"f"_). When the command string corresponds to a combination of single commands, the rover sequentially executes every single command and then returns a string containing its new status.

**Requirement:**
* Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover execute a sequence of single commands and then return a string consisting of its new status.

**Example:** 
* A rover with status _"(0,0,N)"_, after executing the command string _"ffrff"_, returns a string consisting of its new status, namely: _"(2,2,E)"_.

### User Story 7 -- Wrapping
The planet is actually a sphere. Therefore, when the rover goes beyond an edge, its new position is at the opposite edge.
 
**Requirement:** 
* Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover go beyond the edges and then return a string consisting of its new status.
 
**Example:** 
* On a 10x10 planet, a rover with status _"(0,0,N)"_, after executing the command string _"b"_, returns a string consisting of its new status, namely: _"(0,9,N)"_.

### User Story 8 -- Single Obstacle
The rover can encounter an obstacle while executing commands and thus moving on the planet. When this happens, the rover cannot pass through the obstacle (i.e., it does not move). Therefore, it takes note of the encountered obstacle and then tries to continue executing the remaining commands (in the command string). Once all the commands have been executed, the rover returns a string containing its new status and the encountered obstacle. If the same obstacle has been encountered twice or more, it is reported only once.
 
**Requirement:** 
* Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover deal with an obstacle and then return a string containing its new status and the encountered obstacle.
 
**Example:** 
* There is one obstacle on the planet at coordinates _(2,2)_. A rover with status _"(0,0,N)"_, after executing the command string _"ffrfff"_, returns a string containing its new status and the encountered obstacle, namely: "(1,2,E)(2,2)". Note that the same obstacle has been encountered twice but reported only once.

### User Story 9 -- Multiple Obstacles
The rover can encounter multiple obstacles while executing a command and thus moving on the planet. When this happens, the rover (which cannot pass through obstacles) returns a string containing its new status and the encountered obstacle (in the order with which they have been encountered). If the same obstacle has been encountered twice or more, it is reported only once.
 
**Requirement:** 
* Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover deal with more obstacles and then return a string containing its new status and the encountered obstacles.
 
**Example:** 
There are two obstacles on the planet at coordinates _(2,2)_ and _(2,1)_. A rover with status _"(0,0,N)"_, after executing the command string _"ffrfffrflf"_, returns a string containing its new status and the encountered obstacles, namely: _"(1,1,E)(2,2)(2,1)"_. Note that the first obstacle has been encountered twice but reported only once.

### User Story 10 -- Wrapping and Obstacles
The rover can encounter an obstacle when trying to go beyond an edge.
 
**Requirement:** 
* Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover deal with obstacles, when trying to go beyond edges, and then return a string containing its new status and the encountered obstacles.
 
**Example:** 
On a 10x10 planet, there is an obstacle at coordinates _(0,9)_. A rover with status _"(0,0,N)"_, after executing the command string _"b"_, returns a string containing its new status and the encountered obstacle, namely: _"(0,0,N)(0,9)"_.

### User Story 11 -- A Tour Around the Planet
 
The rover takes a tour around the planet, encountering several obstacles and going beyond edges in any dimension.
 
**Requirement:** 
* Implement ```MarsRover.execute_command(self, command_string: str) -> str``` to let the rover take a tour around the planet and then return a string containing its new status and the encountered obstacles.
 
**Example:** 
* On a 6x6 planet, there are obstacles at coordinates _(2,2)_, _(0,5)_, and _(5,0)_. A rover with status _"(0,0,N)"_, after executing the command string _"ffrfffrbbblllfrfrbbl"_, returns a string containing its new status and the encountered obstacles, namely: _"(0,0,N)(2,2)(0,5)(5,0)"_.
