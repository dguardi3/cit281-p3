# cit281-p3

# Project 3: Creating Coin Value Tracker using Node.js and Fastify

### Overview
In this project I used Node.js and Fastify to create a server and create code that can test the value of coin objects and display the total value of different amounts of coins.

### Project Code
```markdown
let validDenomination = (coin) => {
   const denominations =  [1,5,10,25,50,100];
   if (denominations.indexOf(coin.denom) > 1) {
       return true
   } else {
       return false
   }
}

let valueFromCoinObject = (obj) => obj.denom * obj.count;

let valueFromArray = (arr) => {
    let total;

    for (let i = 0; i < arr.length; i++) {
         total = total + valueFromCoinObject(arr[i])
    }

    return total;
}

let coinCount = (coinage) => valueFromArray(coinage);

const coins = [{denom: 25, count: 2},{denom: 1, count: 7}];

console.log(coinCount(coins))

export function ValueFromCoinObject()

 /*
TEST FUNCTIONS

console.log("{}", coinCount({denom: 5, count: 3}));
console.log("{}s", coinCount({denom: 5, count: 3},{denom: 10, count: 2}));
const coins = [{denom: 25, count: 2},{denom: 1, count: 7}];
console.log("...[{}]", coinCount(...coins));
console.log("[{}]", coinCount(coins)); 

*/
```

```markdown
const fs = require('fs');

const fastify = require("fastify")({
    logger: false,
    });

const listenIP = 'localhost';
const listenPort = 8080;

fastify.listen(listenPort, listenIP, (err, address) => {
    
    if (err) {
        console.log(err);
        process.exit(1);
    }


console.log(`Server listening on ${address}`);
});

let pageContent = "";

fs.readFile(`${__dirname}/index.html`, 'utf8' , (err, data) => {
    if (err) {
        console.log(err);
    } else {
        pageContent = data }
  })

fastify.get("/", (request, reply) => {
    reply
    .code(200)
    .header("Content-Type", "text/html; charset=utf-8")
    .send(`${pageContent}`);
    });

    
fastify.get("/coin", (request, reply) => {
    
    let {denom,count} = request.query;

    let coinValue = valueFromCoinObject(request.query)
    
    reply
    .code(200)
    .header("Content-Type", "text/html; charset=utf-8")
    .send(`<h2>Value of ${count} of ${denom} is ${coinValue}</h2><br /><a href="/">Home</a>`);
    });
```
