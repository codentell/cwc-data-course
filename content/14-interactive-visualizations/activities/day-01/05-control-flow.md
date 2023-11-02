+++
title = "05. Control Flow 👩‍🏫🧑‍🏫"
weight = 5
tags = ["plotly"] 
+++

### Conditional References
```javascript
// 1. Simple conditional
if (condition) {
  // do if true
}

// 2. if-else
if (condition) {
  // do if true
} else {
  // do if false
}

// 3. else-if
if (condition1) {
  // do if condition1 is true
} else if (condition2) {
  // do if condition1 is false and condition2 is true
} else {
  // do if condition1 and condition2 are false
}

// 4. logical operators
if (condition1 && condition2) {
  // do only if condition1 and condition2 are true
}

if (condition1 || condition2) {
  // do if either condition1 or condition2 is true
}
```

### Exercise Control Flow
```javascript
let painAfterInjury = true;
let significantSwelling = true;
let ableToWalk = true;
// let painInBothAnkles = true;
// let fever = true;
// let moreThanOneJointSwollenAndRed = true;
// let suddenPain = true;
// let clothingAgainstJoinCausesPain = true;
// let painDuringWeather = true;
// let painAfterUseOfAnkle = true;

if (painAfterInjury && significantSwelling) {
  if (!ableToWalk) {
    console.log("You may have a fracture or sprain.")
    console.log("Don't walk on the injured foot. Raise the leg and place ice on the swollen area.")
    console.log("See your doctor promptly")
  } else {
    console.log("You may have a sprained ankle, or a fracture of the fibula.")
    console.log("Use ice, elevation, rest and an elastic bandage to keep the swelling under control.")
    console.log("See your doctor if the swelling and pain continue.")
  }
} else {
    if (painInBothAnkles) {
      console.log("You may have rheumatoid arthritis")
      console.log("See your doctor. He or she can prescribe medicine to help control the symptoms of rheumatoid arthritis.")
    } else if (fever || moreThanOneJointSwollenAndRed) {
      console.log("Fever along with a painful, swollen joint could be caused by an infected joint. More than one affected joint could mean rheumatic fever.")
      console.log("URGENT. SEE YOUR DOCTOR RIGHT AWAY.")
    } else if (suddenPain || clothingAgainstJoinCausesPain) {
      console.log("You may have gout.")
      console.log("See your doctor. During a gout attack, you should rest in bed. You can put a hot pad or an ice pack on your ankle to ease the pain")
    } else if (painDuringWeather || painAfterUseOfAnkle) {
      console.log("These symptoms could be caused by osteoarthritis or by previous trauma to the ankle.")
      console.log("See your doctor. Use heat and anti-inflammatory medicine to relieve discomfort.")
    } else {
      console.log("For more information, please talk to your doctor. If you think your problem is serious, call right away.")
    }
}
```

### Iterations
```javascript
// Prototypical use case increments loop counter by one on each iteration
for (let i = 0; i < 10; i++) {
  console.log("Iteration #", i);
}

// Looping through an array
let students = ["Johnny", "Tyler", "Bodhi", "Pappas"];

for (let j = 0; j < students.length; j++) {
  console.log(students[j]);
}
```