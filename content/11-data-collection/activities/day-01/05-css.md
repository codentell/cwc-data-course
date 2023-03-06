+++
title = "05. CSS 👩‍🏫🧑‍🏫"
weight = 5
tags = ["scraping"] 
+++

# css demo 01
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>

    <p>I'm first!</p>
    <p>I'm second!</p>

    <p>I'm third!</p>
    <p>I'm fourth!</p>

</body>

</html>
```

# css demo 02
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    
    <style>

    </style>
        
</head>

<body>

    <div>
        <p>I'm first!</p>
        <p>I'm second!</p>
    </div>

    <div>
        <p>I'm third!</p>
        <p>I'm fourth!</p>
    </div>
</body>

</html>
```

# css demo 03
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        .first-half {
            color: red;
        }
    </style>
    
</head>

<body>

    <div>
        <p class='first-half'>I'm first!</p>
        <p class='first-half'>I'm second!</p>
    </div>

    <div>
        <p>I'm third!</p>
        <p>I'm fourth!</p>
    </div>
</body>

</html>
```

# css demo 04

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        .first-half {
            color: red;
        }
    
        #third {
            color: green;
        }
    </style>
    
</head>

<body>

    <div>
        <p class='first-half'>I'm first!</p>
        <p class='first-half'>I'm second!</p>
    </div>

    <div>
        <p id="third">I'm third!</p>
        <p>I'm fourth!</p>
    </div>
</body>

</html>
```