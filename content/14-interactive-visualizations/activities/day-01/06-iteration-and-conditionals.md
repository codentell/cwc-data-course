+++
title = "06.  Iteration and Conditional 👩‍🎓👨‍🎓"
weight = 6
tags = ["plotly"] 
+++

# Movie Profit Looping

In this activity, you will create a for loop, append values into arrays based on a movie's decade, calculate the average profit of all movies, and print out how many of the top 10 movies came from each decade.

## Instructions

Given a list of movie objects in `data.js`, do the following:

* Open the starter file movies.js to edit.

* Append the movies into arrays based on the movie's decade.

* Calculate the average profit of all movies.

* Print how many of the top 10 movies came from each decade.

* Review your results in the DevTools console after opening `index.html` in Chrome.

## Hint

* For more information about how to push elements to an empty array, review 02-Ins_JavaScript-Variables_and_Data_Structures.

*  To find the length of the array, review the [JavaScript Array documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/length) from Mozilla.

## Reference

Wikipedia. Highest-grossing films as of 2020 adjusted for inflation (Accessed November 30, 2021). https://en.wikipedia.org/wiki/List_of_highest-grossing_films

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
### data.js
```javascript
let movies = [
    {
        title: 'Gone with the Wind',
        profit: 3739000000,
        year: 1939
    },
    {
        title: 'Avatar',
        profit: 3286000000,
        year: 2009
    },
    {
        title: 'Titanic',
        profit: 3108000000,
        year: 1997
    },
    {
        title: 'Star Wars',
        profit: 3071000000,
        year: 1977
    },
    {
        title: 'Avengers: Endgame',
        profit: 2823000000,
        year: 2019
    },
    {
        title: "The Sound of Music",
        profit: 2572000000,
        year: 1965
    },
    {
        title: 'E.T. the Extra-Terrestrial',
        profit: 2511000000,
        year: 1982
    },
    {
        title: 'The Ten Commandments',
        profit: 2377000000,
        year: 1956
    },
    {
        title: 'Doctor Zhivago',
        profit: 2253000000,
        year: 1965
    },
    {
        title: 'Star Wars: The Force Awakens',
        profit: 2221000000,
        year: 2015
    }
]

```

### movies.js
```javascript
// Open the inspector to see the data
console.log(movies)

// Starting a profit sum
let sum = 0;

// Arrays to hold all movies by decade
movies1930s = [];
movies1940s = [];
movies1950s = [];
movies1960s = [];
movies1970s = [];
movies1980s = [];
movies1990s = [];
movies2000s = [];
movies2010s = [];

// For loop to go through all movies
for (let i = 0; i < movies.length; i++) {
  // Init variable to hold the current movie in loop
  let movie = movies[i];

  // Increment the sum variable by the amount of profit
  sum += movie.profit;

  // Conditional statements to determine array assignment
  if (movie.year < 1940) {
    movies1930s.push(movie);
  } else if (movie.year < 1950) {
    movies1940s.push(movie);
  } else if (movie.year < 1960) {
    movies1950s.push(movie);
  } else if (movie.year < 1970) {
    movies1960s.push(movie);
  } else if (movie.year < 1980) {
    movies1970s.push(movie);
  } else if (movie.year < 1990) {
    movies1980s.push(movie);
  } else if (movie.year < 2000) {
    movies1990s.push(movie);
  } else if (movie.year < 2010) {
    movies2000s.push(movie);
  } else {
    movies2010s.push(movie);
  }
}

// Find the average profit
let avg = sum / movies.length;

// Print results
console.log("---------");
console.log(`${movies1930s.length} of the top ten highest grossing (adjusted for inflation) movies are from the 1930s.`);
console.log(`${movies1940s.length} of the top ten highest grossing (adjusted for inflation) movies are from the 1940s.`);
console.log(`${movies1950s.length} of the top ten highest grossing (adjusted for inflation) movies are from the 1950s.`);
console.log(`${movies1960s.length} of the top ten highest grossing (adjusted for inflation) movies are from the 1960s.`);
console.log(`${movies1970s.length} of the top ten highest grossing (adjusted for inflation) movies are from the 1970s.`);
console.log(`${movies1980s.length} of the top ten highest grossing (adjusted for inflation) movies are from the 1980s.`);
console.log(`${movies1990s.length} of the top ten highest grossing (adjusted for inflation) movies are from the 1990s.`);
console.log(`${movies2000s.length} of the top ten highest grossing (adjusted for inflation) movies are from the 2000s.`);
console.log(`${movies2010s.length} of the top ten highest grossing (adjusted for inflation) movies are from the 2010s.`);
console.log(`The average movie profit (adjusted for inflation) is ${avg}.`);
console.log("---------");
```
{{ % expand %}}
