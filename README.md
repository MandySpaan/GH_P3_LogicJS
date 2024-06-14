## Assignment 📝

The goal of this project was to calculate how to achieve the best deal for an empanada promotion. <br>
The following factors had to be taken into consideration:

- Promotion: get 3, pay only 1
- The 1 to be paid is the most expensive of a group of 3
- You can buy a maximum of 40 empanadas in total
- The total of empanadas has to be dividable by 3
- There are 3 different options, priced €12, €14 & €16
- You can combine the empanadas ordering half / half:
  - For example: if you have 1x €12, 1x €14 and 1x €16 <br>
    Then 1x €12 and 1x €16 can be combined to reach<br>
    a lower price of the most expensive empanada:<br>
    - 0.5x €12 + 0.5x €16 = a new empanada worth €14<br>
      which when ordered twice has the same content<br>
      So 1x €12 and 1x €16 can be turned into 2x €14<br>
      By making this combination, in the example, the highest <br>
      price (and thus the best deal) became €14 instead of €16.

You can find the full assignment (in Spanish) in the file [assignment.md](assignment.md).

The following repository was cloned to be used a starting point: [the Empanada Challenge](https://github.com/GeeksHubsAcademy/javascript-empanadas-challenge).<br>
This repository includes the following initial files:

- A main.js file with an empty function that takes 3 parameters (a, b, c)
  - These parameters represent the quantity of empanadas <br>
    (a) respresents priced at €12, (b) at €14 and (c) at €16
- A main.test.js file that holds the tests that need to be completed

## My Thought Process 💭

The overall idea of how to get to the desired result:

- Step 1: Translate the given input properties <i>(a, b, c)</i> into an array of items, where each item represents an empanada named as it's own price: <i>arrayEmpanadas</i>.
- Step 2: Take <i>arrayEmpanadas</i> with the original prices and calculate the possible combinations to get to a new outcome of price per empanada. The new price per empanada has to turn the highest prices as low as possible. Then place these new prices into a new array: <i>combinedPrices</i>.
- Step 3: Take the array <i>combinedPrices</i> and organize the order of its content (new price per empanada) from highest to lowest.
- Step 4: From this now organized array <i>combinedPrices</i>, select chronologically every first of groups of three, and put this into a new array: <i>toBePaid</i>. This array now includes all the empanadas that have to be paid.
- Step 5: Add all the items from the <i>toBePaid</i> together to come to the final price.

## Notes on JS Code 💻

For the sake of better understanding of how the code gets to the final result, I have added console logs at all steps earlier mentioned in [My Thought Process 💭](#my-thought-process-).

### Some parts of the code singled out with explanation

To get from <i>arrayEmpanadas</i> to the array <i>combinedPrices</i>, I've made use of a while loop:

```javascript
while (arrayEmpanadas.length / 2 >= 1) {
  var newPrice = (arrayEmpanadas.at(0) + arrayEmpanadas.at(-1)) / 2;
  combinedPrices.push(newPrice, newPrice);
  arrayEmpanadas.shift();
  arrayEmpanadas.pop();
}
```

As long as there were 2 items (empanadas) left in the original array <i>arrayEmpanadas</i>, I would take the first item (lowest price) and last item (highest price) and divide them through 2 to get to a new price saved in var <i>newPrice</i>. Then <i>newPrice</i> would get pushed twice into the new array <i>combinedPrices</i>. And the first and last item of the old array <i>arrayEmpanadas</i> would get deleted using shift and pop.

After this I added an if statement, in case of the total number of items (empanadas) being uneven:

```javascript
if (arrayEmpanadas.length === 1) {
  var newPrice = arrayEmpanadas.at(0);
  combinedPrices.push(newPrice);
  arrayEmpanadas.pop();
}
```

This makes sure that if there is only 1 item (empanada) left, even though this item can not be combined, it does get added to the new array <i>combinedPrices</i>.

---
