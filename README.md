# cit281-p1

# Project 1: Practicing CLI Commands and coding Javascript

### Overview
In this project I used CLI commands to create an array of folders. I also gained experience writing and executing Node.js Javascript code.

### Project Code
```markdown
/*
    CIT 281 Project 1
    Name: Devin Guardino
*/

// Returns a random number between min (inclusive) and max (exclusive)
function getRandomInteger(min, max) {
    return Math.floor(Math.random() * (max - min) + min);
}

const alphabet = "abcdefghijklmnopqrstuvwxyz".split("");
let result = "";

for (let i = 0; i < getRandomInteger(5, 26); i++) {
    result += alphabet[getRandomInteger(1,alphabet.length-1)];
}

console.log(result);
```

```markdown
const date = new Date();
const days= ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

console.log(days[date.getDay()]);
```
