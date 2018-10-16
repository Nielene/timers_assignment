# Rock, Paper, Scissors
const readline = require('readline');

const reader = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

const cpu = () => {
let comp = Math.random();
  if (comp >= 0.0 && comp <= 0.33){
    return "r"
  } else if (comp >= 0.34 && comp <= 0.66) {
    return "p"
  } else if (comp >= 0.67 && comp <= 1) {
    return "s"
  }
}

const game = (res, comp) => {
  if( (res === "r" && comp === "s") || (res === "s" && comp === "p") || (res === "p" && comp === "r")) {
    return `Congratulations! You win!`
  } else if ( (res === "r" && comp === "p") || (res === "p" && comp === "s") || (res === "s" && comp === "r")) {
    return `You lost. Try again!`
  } else if ((res === "r" && comp === "r") || (res === "p" && comp === "p") || (res === "s" && comp === "s")) {
    return `We tied!`
  }
};

// let gamePossibilities = {
//   win: [['r', 's'], ['p', 'r']]
// }
//
// if (gamePossibilities.win.includes([userChoice, computerChoice])) {
//   // print you win
// }

reader.question(`Welcome to rock, paper, scissors! \n Please type 'r', 'p', or 's' to make a choice. \n`, (res) => {
  // console.log(`you chose: ${res}`)
  let cpuChoice = cpu()
  console.log(`You chose ${res}. Hmm...`)
  setTimeout (() => {
    console.log(`The computer chose: ${cpuChoice}.`)
    console.log(game(res, cpuChoice));
  }, 5000);
  reader.close();
});

// code syntax = order of code (what goes where?)
//1. console greeting ("wel..come")
//2. space for user's choice [reader.prompt]?
//3. set time out (~5 seconds)
//4. use math.random to display comp choice
//5. use conditional to compare user n comp choices
//6. return win, loss or tie result
//7.


## Bonus

[Eliza](http://psych.fullerton.edu/mbirnbaum/psych101/Eliza.htm) is one of the world's first chatbots. She uses the user's response to come up with a question, mimicking a not-so-insightful therapist. She never says anything herself - she simply picks a detail the user wrote and asks a new question. Play around with her in the link above and see how this works.

Your task is to use `readline` to **write a simple version of Eliza** - a chatbot that can handle any input and return an at-least-sort-of-relevant question.

*Hint*: When the user says "I" or "I'm" or any word referring to themselves, that's a dead giveaway that the next thing they write will be useful to your response.
