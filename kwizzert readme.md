# Kwizzert

This README will give you a short summary of the Kwizzert App. We start with a walkthrough into getting this project up and running. Further we will list the requirements, architecture, communication protocol, components, routes and external libraries used.

Kwizzert is a real-time web-app supposed to be used as an party game for groups of people setting up and taking quizzes, a pub quiz.

A more extensive description of the app can be found in [Kwizzert Description.pdf](example)

### Version
0.1.3

## Installation
```
git clone https://github.com/example
npm install
npm start
```
## Requirements
### Teams
The teams app will restrict players in the following ways
 - Team sizes do not matter
 - Teams can join a game with the provided password
 - Teams can only join at the beginning of a game
 - Two teams need to sign up but there can be more participating teams
 - A game consists of multiple rounds and each round has 12 questions
 - Questions can be selected from 3 categories
 - The team app can be used on smartphones
 - Team names are unique and required
 - Teams can edit their answer after submitting it

### Kwizmaster
The kwizmaster app will enable the kwizmaster to do the following
 - Verify team submissions
 - Start a game
 - Select the 3 categories for the question of that round
 - Verify whether answers submitted by the participating teams are valid or not
 - Skip a question
 - End a game
 - Select the next question
 - The app can be used on tablets

### Scoreboard
The scoreboard app will display the following information
 - The points of the teams
 - The time left to answer a question
 - What state the game is in
 - The round
 - The question
 - Team names and the scores of these teams
 - The amount of correct answers this round
 - The category of the question
 - Live updates on verification input of the quiz master
 - The winning team after a game/round has ended
 - Can be used on a regular screen

### Other
 - Multiple games will be supported simultaneously
 - There will be no duplicate questions during games
 - Empty answers are ignored

### Optional Requirements
 - Questions are time limited
 - The App keeps a history of played games
 - The database stores the game data so games can be paused and picked up again at an later date

## Mockups
The game has several states it can cycle through. Based on the input of the game master, the scoreboard and the team app will display status messages or navigate to new pages.

State examples:
- Pre Game
- Pre Round
- Pre Question
- Question
- Post Question

Flow examples
1. GM starts game ->
2. Signups of teams (Pre Game) ->
3. GM selects categories for current round (Pre Round) ->
4. GM selects the question (Pre Question) ->
5. The teams submit answers (Question) ->
6. The GM closes submissions and validates answers (Post Question) ->
7. The GM selects next question (Question Setup) -> 4

The game will repeat the 4-7 12 times after which it will drop back into 3. Pre Round and the scoreboard will update the current scores.

An example of what the apps will look like can be found [here](example).

## Architecture
### Component Diagram
This component diagram describes what components the Kwizzert exists out of. It also shows the connection between the several components and the interfaces that are used by the components to exchange data.
![Component Diagram](example)

### Deployment Diagram
This deployment diagram shows the physical distribution of the components. It also describes which protocol(s) the communication between the several nodes exists of.
![Deployment Diagram](example)

### Component Descriptions
Component|Description
---|---
Kwizzert | Main application that serves all three Single Page Applications. Uses NodeJs.
ScorebordSPA | Single Page Application for the scoreboard app. React application.
TeamSPA | Single Page Application for the teams app. React application.
KwizmasterSPA | Single Page Application for the quiz master app. React application.
BusinessLayer | Handles all database interactions with help of Mongoose.
MongoDB | Database to store information for the Kwizzert

### Architectural Decisions
Decision | Motivation
--- | ---
Three-tier architecture | To ensure the application can handle a great amount of users and running games the decision to use a three-tier architecture has been made. More information on tiered architecture can be found [here](https://msdn.microsoft.com/en-us/library/ee658120.aspx).

## Communication Protocol
The communication between the business layer and the SPA's will be done through a REST API. For now, the only functionality this API offers is getting the list of questions for a specific category, getting the details for a specific question id and getting a list of all possible categories.

#REDACTED

## React Components
Here you can find a list of planned components, we plan to split jsx and logical code staying true to the MVVM pattern, communication with the server will not be split and lives in the controller of the specific page.

### Quiz Master

Header -
Lets the quiz master end a game, displays the current round/ question.

CreateGame -
Lets the quiz master register a new game, server will communicate whether the game name is accepted.

GameSetup -
Shows the quiz master teams that sign in to the game, quiz master can select which teams are allowed to join and can start the game.

RoundSetup -
Lets the quiz master pick categories out of available categories.

QuestionSetup -
Lets the quiz master pick a question out of selected categories, by default a random question will be selected, selected questions will be removed from the question list.

QuestionProgress -
Shows the quiz master team submissions and lets the game master close submissions

PostQuestion -
Lets the quiz master verify whether answer are correct or not.

### Team

Header -
Displays the current round/ question.

Signup -
Lets the team signup for a game with submitted team name.

Status -
Used when there is no input needed from teams, shows a short message about the current state of the game.

Question -
Lets the team submit and edit an answer.

### Scoreboard

Header -
Displays the current round/ question.

Signin -
Lets the scoreboard connect to a game.

Status -
Displays the scores, correct answers, current state and team names.
Also displays the category, question and answer.

PostGame -
Displays a leaderboard, top 3 winning teams will be emphasized.

## Routes
The following routes are available, bookmarking or manually typing in an URL will redirect users to the initial page.
/team/, /master/ and /scoreboard/ are serverside routing, all other routing will be done clientside.

``/team/join`` <br>
Team UI to join a game.

``/team/:gameID/:teamId`` <br>
Team UI for a running game.

``/master/create`` <br>
Kwizmeesterst UI for creating a new game.

``/master/:gameID`` <br>
Kwizmeestert UI for a running game.

``/scoreboard/connect`` <br>
Scoreboard UI for connecting a scoreboard to a running game.

``/scoreboard/:gameID`` <br>
Scoreboard UI for a running game.

## External libraries
Libary name | Version
--- | ---
[NodeJS](https://nodejs.org/en/) | 6.10.1
[MongoDb](https://www.mongodb.com/) | 3.4.3
[Mongoose](http://mongoosejs.com/) | 4.9.3
[React](https://facebook.github.io/react/) | 15.4.2
[React-router](https://github.com/ReactTraining/react-router) | 4.0.0
[Ws](https://github.com/websockets/ws) | 2.2.2
[Bootstrap](http://getbootstrap.com/) | 3.3.7
[Express](https://expressjs.com/) | 4.15.2
