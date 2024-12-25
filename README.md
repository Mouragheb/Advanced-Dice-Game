# Advanced Dice Game HTML/CSS/JS

A Pen created on CodePen.io. Original URL: [https://codepen.io/Mouragheb/pen/YPKQjoK](https://codepen.io/Mouragheb/pen/YPKQjoK).

Project Overview: Advanced Dice Game

This project is an interactive dice game implemented using HTML, CSS, and JavaScript. It allows players to simulate a turn-based dice game with specific rules and scoring criteria, providing an engaging and responsive gaming experience.

Core Features:
	1.	Game Rules:
	•	Six rounds per game.
	•	Three dice rolls allowed per round.
	•	Players can choose a score option after rolling the dice.
	•	Various scoring categories (e.g., Full House, Small Straight, Large Straight).
	2.	Dynamic Dice Rolling:
	•	Dice values are generated randomly upon clicking a button.
	•	Scores are calculated based on the rolled values and game rules.
	3.	Interactive UI:
	•	Dynamic update of scores, rounds, and dice values.
	•	Players select scoring options via radio buttons.
	4.	Game Logic:
	•	Includes checks for combinations like “Three of a Kind,” “Full House,” “Small Straight,” and “Large Straight.”
	•	Updates player scores and tracks the game’s progress.

Technologies and Languages Used:
	1.	HTML:
	•	Used for structuring the webpage and game layout.
	•	Includes elements like buttons, headers, and forms.
	•	Example:

<button class="btn" id="roll-dice-btn" type="button">Roll the dice</button>


	2.	CSS:
	•	Provides the visual styling for the game.
	•	Implements responsive design using media queries.
	•	Uses custom CSS variables for consistent color themes.
	•	Example:

.btn {
  cursor: pointer;
  color: var(--black);
  background-color: var(--gold);
}


	3.	JavaScript:
	•	Implements the game logic, event handling, and interactivity.
	•	Generates random dice values and checks scoring conditions.
	•	Example:

const rollDice = () => {
  diceValuesArr = [];
  for (let i = 0; i < 5; i++) {
    const randomDice = Math.floor(Math.random() * 6) + 1;
    diceValuesArr.push(randomDice);
  }
  listOfAllDice.forEach((dice, index) => {
    dice.textContent = diceValuesArr[index];
  });
};

Key Functionalities:
	1.	Rolling the Dice:
	•	A button triggers the rolling of dice, simulating random values between 1 and 6.
	•	Example:

rollDiceBtn.addEventListener("click", () => {
  rollDice();
});


	2.	Score Calculation:
	•	Detects specific patterns in dice values (e.g., “Full House,” “Small Straight”).
	•	Updates the corresponding score option dynamically.
	•	Example:

const detectFullHouse = (arr) => {
  const counts = {};
  for (const num of arr) {
    counts[num] = counts[num] ? counts[num] + 1 : 1;
  }
  const hasThreeOfAKind = Object.values(counts).includes(3);
  const hasPair = Object.values(counts).includes(2);
  if (hasThreeOfAKind && hasPair) {
    updateRadioOption(2, 25);
  }
};


	3.	User Interaction:
	•	Players choose scoring options using radio buttons.
	•	Buttons allow users to roll the dice or keep the score for the round.
	•	Example:

keepScoreBtn.addEventListener("click", () => {
  let selectedValue;
  for (const radioButton of scoreInputs) {
    if (radioButton.checked) {
      selectedValue = radioButton.value;
      break;
    }
  }
  if (selectedValue) {
    updateScore(selectedValue, achieved);
  }
});


	4.	Game Rules Toggle:
	•	A “Show Rules” button toggles the visibility of the rules container.
	•	Example:

rulesBtn.addEventListener("click", () => {
  isModalShowing = !isModalShowing;
  rulesContainer.style.display = isModalShowing ? "block" : "none";
});

Summary:

The project demonstrates a well-structured implementation of a turn-based dice game. It uses:
	•	HTML for content and layout.
	•	CSS for styling and responsive design.
	•	JavaScript for interactivity and game logic.

It combines randomization, event handling, and conditional logic to create an engaging experience for players.

Example Scenarios:
	1.	Rolling the Dice:
	•	Players click the “Roll the Dice” button to generate random values for five dice.
	2.	Detecting Patterns:
	•	If the dice values are [1, 2, 3, 4, 6], the program identifies a “Small Straight” and updates the score option with 30 points.
	3.	Keeping Score:
	•	After selecting a score option (e.g., “Small Straight”), the player’s total score is updated, and the next round begins.

Highlights:
	•	Customizability: The game logic can easily be extended with additional scoring rules.
	•	Responsive Design: CSS ensures the game is playable on various screen sizes.
	•	Dynamic Interactions: JavaScript brings the game to life by updating elements in real-time based on user actions.
