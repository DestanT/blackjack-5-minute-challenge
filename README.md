# Blackjack: 5 Minute Challenge

## Table of Contents
1. [Introduction](#introduction)
2. [User Stories](#user-stories)
3. [Features:](#features)
    1. [First Visit](#first-visit)
    2. [The Deck Of Cards](#the-deck-of-cards)
    3. [The 'Hit', 'Split' and 'Stand' Functions](#the-hit-split-and-stand-functions)
        - [Hit](#hit)
        - [Split](#split)
        - [Stand](#stand)
    4. [The Poker Chips and Betting](#the-poker-chips-and-betting)
    5. [End Game Score Screen](#end-game-score-screen)
    6. [Animations](#animations)
    7. [Sound Effects](#sound-effects)


4. [Testing, Struggles, and Future Features](#testing-struggles-and-future-features)
    1. [Testing](#testing)
    2. [Bugs/Challenges](#bugschallenges)
5. [Feature Ideas For The Future](#feature-ideas-for-the-future)
7. [Technologies Used](#technologies-used)
8. [Deployment](#deployment)
9. [Development](#development)
10. [Credits](#credits)
    1. [Content](#content)
    2. [Media](#media)

## Introduction

This card game is primarily intended for someone who is already quite familiar with the casino game "Blackjack". A summarised ruleset is present for new players and anyone wanting to familiarise themselves with the game. A link to the full ruleset can also be found.

The idea of the game is for the player to reach the highest possible score in 3 minutes and to compete for a higher score each time. The quick 3 minute nature of the game rounds means players can spend a small amount of time as downtime, during commuting or while waiting for someone.

As a player, I would seek to beat my own high score every time I play. I would also share the game with my friends to add to the competitive nature of the game and let know what high scores I was able to achieve. The high risk, high reward nature of any casino game drives this attention naturally.

You can view the deployed website by clicking [**here**](https://destant.github.io/blackjack-3-minute-challenge/).

## User Stories

As a user of the site I would:
* Enjoy spending a few minutes every so often to play blackjack
* Return to the site to beat my high score
* Share the site with friends so that I could compete with them
* Screenshot the end screen with my top 3 high scores on it to show off to my friends and colleagues

As the developer of the site I would:
* Listen to feedback from my users and add updates to include new features accorgindly
* Fix bugs, as they are reported to me

## Features:

### First Visit
![Input Name Pop-Up](/documentation/input-name-screen.png)
* On the first visit the player is greeted with this pop up modal window.
  * Player must input their name (minimum 2 characters, maximum 15).
  * The name is stored in localStorage.
  * The 'Game Rules' will display the player's name.\
  ![Greeting Player](/documentation/hi-player-name.png)
* On subsequent visits (i.e. if localStorage already has name data), the game will welcome the player back.\
![Welcome Back Player](/documentation/welcome-back-player-name.png)
* If the player wishes to change their name; they can click on their name in the 'Game Rules' section.

### The Deck Of Cards
The deck of cards is displayed on the side of the screen.
* It has a 'remaining' cards counter
* When the deck is below 15, it will reshuffle into a new deck
* It isn't explicitly stated, but the choice behind having a remaining card counter and only using one deck of cards was primarily because I wanted to give observant players an edge when it comes to card counting.\
![Draw Deck](/documentation/draw-deck.png)

### The 'Hit', 'Split' and 'Stand' Functions

#### __Hit__
![Hit Function](/documentation/function-hit.png)
![Player Sum](/documentation/player-sum.png)
* As long as the player has a sum below 21 the 'Hit' function allows the player to draw another card.
* Aces are automatically considered at their higher value of 11.
  * When the player exceeds 21 and holds an ace(s), one ace at a time is automatically recalculated to be worth 1 instead until a score of 21 or below is reached.
* If the player exceeds 21; the round is automatically lost and the 'awww' sound effect is played.
  * The 'Deal' button is revealed to deal out the new round.\
![Deal Button](/documentation/deal-button.png)

![Blackjack, 21](/documentation/perfect-score.png)
![Player Sum 21](/documentation/player-sum-21.png)
* When the player has 21 points exactly, the 'Hit' button will grey out and stop functioning.
  * This is to stop accidental clicks when the player has the best score.

#### __Split__
![Split Function](/documentation/function-split.png)
* If two identical cards are dealt at the beginning of a round, the 'Split' button will appear.
  * Players can decide to split or continue playing as normal.

![Split Function Pressed](/documentation/after-split.png)
* If the player decides to split, the left card is put aside (as seen in image - bordered in red).
  * A side bet, matching the original bet, is created (as seen in image - blue border).
    * Split bets can only be initiated if the player has enough cash to match original bet.
  * The 'Player Sum' is updated (green border).
* Once the first card is played, the second card is put into play.

#### __Stand__
* Once the player is happy with their score, they can choose to 'Stand'
  * This initiates the dealers turn:
    * The dealer will automatically draw cards until their obligation to score at least 17 is met.
  * Once the dealer has had their turn:
    * If dealer is bust (score above 21); player wins and cashes out double their bet.
    * Likewise; if the player has a higher score than the dealer.
      * The winning 'ding' sound is played.
      * The 'You Won!' text pops up for 1.5s below the 'Player Sum'.\
      ![Win Text](/documentation/win-text.png)
    * If dealer exceeds the player score; the player loses and loses their bet.
      * The 'Awww' sound effect is played.
      * The 'You Lose.' text pops up for 1.5s below the 'Player Sum'.\
      ![Lose Text](/documentation/lose-text.png)
    * In case of a draw; nobody wins, the player retains their bet.
      * The 'Draw!' text pops up for 1.5s below the 'Player Sum'.\
      ![Draw Text](/documentation/draw-text.png)

### The Poker Chips and Betting
![The Poker Chips](/documentation/poker-chips.png)
* The player can click on the poker chips to add to or remove from their bet\
![Total Bet Value](/documentation/total-bet.png)
* Players can only remove a bet in multiples of $100 (as seen in the image; the white poker chip)
  * It is still possible to remove bets below $100. The game checks for this and adjusts accordingly.
* Cash value and bet value is adjusted with every click.
* Animations of chips moving to and from the bet value and hand are played.
* Poker chips will grey out when the player is not allowed to interact with them. And toggle back on when the player can again interact with them.\
![Greyed Out Poker Chips](/documentation/grey-poker-chips.png)

### End Game Score Screen
![Score Screen](/documentation/score-screen.png)
* Once the 3 minute timer runs out at the top of the screen the game will stop and the player will be greeted with the 'Score Screen'
  * The player's cash value, bet value and (if they have) their side bet value will be tallied up.
  * The total will be stored on localStorage and compared. The top 3 scores will be shown on the scoreboard.
  * If the player has beaten their past high score they will be greeted with a 'Well Done' and an update of their scoreboard\
  ![Beating The Highscore](/documentation/well-done-score-screen.png)
  * If the player failed to beat any of their high scores, they will be greeted with a 'Better luck next time!':\
  ![Better Luck Next Time](/documentation/next-time-score-screen.png)
  * If the player runs out of money before the timer is finished, they will be greeted with this screen instead:\
  ![No Money Score Screen](/documentation/no-money-score-screen.png)
* If the player has had enough before the timer ends, or simply wishes to record their highscore without risking further losses, then the 'End Game' button can be pressed next to the timer at the top of the screen:\
![End Game Button](/documentation/end-game-button.png)

### Animations
The animations were done using elements of all three; HTML, CSS and JavaScript. There are currently animations for:
* Poker chips being placed as bets, all in their individual colours.
* Poker chips being deducted from the current bet (Two $50 chips can be seen being withdrawn).
* Single cards being dealt to each the dealer and the player.
 
Example Animations:
  * Cards being dealt:\
![Card Animations](/documentation/card-animations.png)
  * Poker chips being withdrawn from the bet:\
![Poker Chip Animations](/documentation/chip-animations.png)

### Sound Effects
There are currently 10 different sound effects in the game, these are:
 * For dealing a single card.
 * When the dealer flips their facedown card to face up.
 * A 'ding' for when the player wins a hand.
 * An 'awww' for when the player loses a hand.
 * Deck shuffle.
 * Two distinctive sounds for when placing a bet..
 * ..and when deducting from a bet.
 * Glass smashing - when the player 'busts' their hand (exceeds 21).
 * A 'boing' sound for when the player does something they shouldn't.
 * And finally a sound of poker chips being pushed around for when the player collects their winnings.

## Testing, Struggles, and Future Features

### __Testing__

__Lighthouse Tests__
* Desktop:\
![Lighthouse Test Desktop](/documentation/lighthouse-desktop.png)
* Mobile:\
![Lighthouse Test Mobile](/documentation/lighthouse-mobile.png)

__JSHint__
* Configurations used:\
![JSHint Configurations](/documentation/jshint-configuration.png)
* Metrics:\
![JSHint Metrics](/documentation/jshint-metrics.png)
* No errors.

__Validator Testing__

RECHECK THIS!

- HTML - No errors or warnings to show. Link to report [here](https://validator.w3.org/nu/?doc=https%3A%2F%2Fdestant.github.io%2Fblackjack-5-minute-challenge%2F).
- CSS - No errors found. Link to report [here](https://jigsaw.w3.org/css-validator/validator?uri=https%3A%2F%2Fdestant.github.io%2Fblackjack-5-minute-challenge%2F&profile=css3svg&usermedium=all&warning=1&vextwarning=&lang=en).
- JavaScript - No errors found. ADD PICTURE HERE + TALK ABOUT CONFIGURATIONS OF TEST.

__Friends and Family Testing__

The project was also tested by friends and family; using their native web browsers for responsiveness using these devices/tools:
  * Monitor 25" screen
  * Windows laptop 15" screen
  * iPhone 12 Pro Max
  * OnePlus 8
  * iPad Pro 12.9" screen
  * iPad Pro 11" screen
  * Chrome dev tools for various other options

### __Bugs/Challenges__

__Challenges__

The biggest challenge of this project was realising that a global leaderboard was not as simple as 'simply uploading data to the internet'. I learned a global leaderboard would require a server and a database of some sort (in this case a simple text/JSON file would have sufficed).

I even went as far as purchasing a Raspberry Pi to serve this purpose and did a substantial amount of research on how to 'build' a server. After everything, the part at which I felt I needed to let go of this ambition (for now!), is when I realised that github pages would only communicate with a server over HTTPS. My server would have only been on HTTP, and that extra layer of complexity, and given the time I had to finish the project meant I had to unfortunately postpone my ambition to create a global leaderboard.

__Unfixed Bugs__

* I have found that even though the same browser and version (Chrome - 113.0.5672.63) were being used, that on some laptops the 'Game Rules' section's scroll feature was not functioning as intended, instead the entire section was on display and viewing the bottom of the game rules meant users that were affected had to 'scroll away' from the game. Image of proper function below:\
![Scroll Bug](/documentation/bugs-rules-scroll.png)

### __Feature Ideas For The Future__

## Technologies Used

* HTML
* CSS
* JavaScript
* Procreate (iPad)
* Endless Paper (iPad)

## Deployment

The project was deployed on GitHub pages from the 'Main Branch Source Code' using the following steps:
* 'git add .', 'git commit" and 'git push' commands were issued one final time when the project was ready and finished.
* On Github the repository for the project was selected.
* Click the 'Settings' tab.
* On the left; select 'Pages'.
* From here; select the source as 'Main Branch'.
* Click 'Save'.

GitHub may take a few minutes to deploy the website so be patient.

The live link to my project can be found [**here**](https://destant.github.io/blackjack-5-minute-challenge/).

## Development

Should anyone wish to add to the project, please feel free to open a new workspace within its current state; then commit and push any changes to the main branch. I will review and add them to the main branch as soon as possible. Thank you!

Should anyone wish to copy and paste the project - you are also welcome to - please remember to give me some credit!

## Credits 

### __Content__

* The wireframe was made using the [Endless Paper App](https://endlesspaper.app/) on the iPad.
* To help me find and visualize the font I used [Fontjoy](https://fontjoy.com/).
* [W3Schools](https://www.w3schools.com/), [Stack Overflow](https://stackoverflow.com/), [Mozilla Dev Tools](https://developer.mozilla.org) was referred to a lot for general syntax and whenever I was stuck on a bug for a while - other similar experiences helped me build a better app.
* [FontAwesome](https://fontawesome.com/) for the "X" mark in the pop-up modal.

### __Media__

* The poker chip images are from [PngAAA](https://www.pngaaa.com/).
* The playing cards .png are from [Super Dev Resources](https://superdevresources.com/free-playing-cards-set/).
* The sound effects are from [Epidemic Sound](https://www.epidemicsound.com/).
* To compress .PNG [CompressPNG](https://compresspng.com/).