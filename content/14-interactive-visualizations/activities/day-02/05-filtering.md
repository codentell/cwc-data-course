+++
title = "05.  Filtering 👩‍🎓👨‍🎓"
weight = 5
tags = ["plotly"] 
+++

# Filtering

In this activity, you will create a custom function by using `filter()` to return the players who made the team, according to the `roster` dataset. Then, you’ll use that filtered data to determine how many players made the cut.

## Instructions

* Use the starter files `index.html` and `filter.js` provided in the [Unsolved](Unsolved) folder.

* Create a custom function to return players who made the team.

* Determine how many players made the cut.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```js
// An array of objects
let roster = [{
  name: "Doug",
  position: "Quarterback",
  madeTeam: true
},
{
  name: "Antonio",
  position: "Tight End",
  madeTeam: true
},
{
  name: "Nick",
  position: "Kicker",
  madeTeam: false
},
{
  name: "Ereck",
  position: "Offensive Live",
  madeTeam: false
},
{
  name: "AJ",
  position: "Line Backer",
  madeTeam: true
}
];
 
// Create a custom function to return players who made the team
function madeCut(player) {
  // return player.madeTeam == true;
  // A more concise way to express a boolean conditional
  return player.madeTeam;
}

// Call the custom function with filter()
let playersOnTeam = roster.filter(madeCut);

// Display the results
console.log(playersOnTeam);

// Determine how many players made the cut
let numberOfPlayers = playersOnTeam.length;

// Display the results
console.log(`${numberOfPlayers} players made the team.`);
```
{{% /expand%}}