# Section 2: JavaScript Language Basics

This is revision of the basic features in JavaScript.

### simple assignment

```js
    var firstName = "John";
    console.log(firstName);
```

.

```js
 var lastName = "Smith";
 var age = 28;
 console.log(firstName + ' ' + lastName + ', age = ' + age);
```

.

```js
 var fullAge = true;
 console.log(fullAge);
```

.

```js
 var job, isMarried;
 console.log(job); // prints undefined

 job = 'teacher';
 isMarried = false;
 console.log(job + ', married: ' + isMarried);
```

### variable mutation

```js
 age = 'twenty eight';
 console.log(age);
```

.

```js
 var john = 33;
 var mark = 28
 
 // logical operators
 var johnOlder = john > mark;
 console.log(johnOlder);  // returns true
```

### `typeof` operator

```js
 console.log(typeof johnOlder);  // returns boolean
 console.log(typeof john);  // returns number
 console.log(typeof age);  // returns string
 var x;
 console.log(typeof x);  // returns undefined
```

### Operator precedence

[Operator precedence list](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)

```js
 var now = 2019;
 var johnBorn = 1987;
 var fullAge = 18;
 
 // Multiple assignments
 //precedence in this case - beats >=
 var isFullAge = now - johnBorn >= fullAge;
 console.log(now - johnBorn);
 console.log(isFullAge);
```

Grouping is the highest precedence (beats division).

```js
 var ageJohn = now - johnBorn;
 var ageMark = 35;
 
 // var average = ageJohn + ageMark / 2;  // this won't work, gives us: 49.5
 var average = (ageJohn + ageMark) / 2;  // this will work, gives us 33.5
 console.log(average);
 
 var a,b;
 a = (3 + 5) * 4 - 6;  // 8 * 4 // 32 - 6 // 26
 console.log(a);
```

We can also assign the value of a to b.

Assignment actually works right to left in this case.

```js
 a = b = (3 + 5) * 4 - 6;  // 8 * 4 // 32 - 6 // 26
 console.log(b);  // 26
```

### More operators

```js
 // a = a * 2; simpler to do this,
 a *= 2;
 console.log(a);  // 52
 
 a +=10;
 console.log(a);  // 62
 
 // can do, a = a + 1; or a += 1; or even better,
 a++;
 console.log(a);  // 63
 
 a--;
 console.log(a);  // 62
```

### Coding challenge 1

Mark and John are trying to compare their BMI (Body Mass Index), which is calculated
using the formula: BMI = mass / height^2 (or mass / (height * height)). (mass in kg and height in metres).

1. Store Mark and John's mass and height in variables.
2. Calculate both their BMI's.
3. Create a boolean variable containing information about whether Mark has a higher BMI than John.
4. Print the results.

```js
 var markMass = 78;
 var markHeight = 1.69;
 var johnMass = 92;
 var johnHeight = 1.95;
 
 var markBmi = markMass / (markHeight * markHeight);
 var johnBmi = johnMass / (johnHeight * johnHeight);
 console.log("Mark's BMI: " + markBmi);
 console.log("Johns's BMI: " + johnBmi);
 var isMarksBmiHigher = markBmi > johnBmi;
 if (markBmi > johnBmi) {
  console.log("Marks's BMI is higher than John's.");
 }
 else {
  console.log("Marks's BMI is lower than John's.");
 }
```

#### Results

> Mark's BMI: 27.309968138370508        
> Johns's BMI: 24.194608809993426       
> Marks's BMI is higher than John's.

### if / else statements

```js
 var name = "John";
 var status = "single";
 
 if (status === "married") {
  console.log(name + " is married.");
 } else {
  console.log(name + " is not married.");
 }
```

### Boolean logic

```js
 var name = "John";
 var age = 16;
 
 if (age < 13) {
  console.log(name + " is a boy.");
 } else if (age >= 13 && age < 20) {
  console.log(name + " is a teenager.");
 } else if (age > 20 && age < 30) {
  console.log(name + " is a young man.");
 }
 else {
  console.log(name + " is a man.");
 }
```

### The Ternary operator and switch statement

```js
 var name = "John";
 var age = 16;
 
 age >= 18 ? console.log(name + " can drink a beer.") : console.log(name + " can drink a fruit juice.\n");
```

#### Results

> John can drink a fruit juice.

```js
 // a better use of the ternary operator
 var drink = age >= 18 ? "beer" : "fruit juice";
 console.log(name + " can drink a " + drink + "\n");  // John can drink a fruit juice.
```

### Switch statement

```js
 var job = 'teacher';
 
 switch (job) {
  case 'teacher':
   console.log(name + " teaches kids how to code.\n");
   break;
  case 'driver':
   console.log(name + " drives kids to school.\n");
   break;
  case 'driver':
   console.log(name + " designs websites.\n");
   break;
  default:
   console.log(name + " has no job.\n");
 }
```

#### Results

> John teaches kids how to code.

### Truthy and falsy values

falsy values are: undefined, null, 0, '', NaN

```js
 var height;
 height = 0; // if the value is 0 the the result is: Variable has NOT been defined.
 
 if (height) {
  console.log("Variable is defined.");
 } else {
  console.log("Variable has NOT been defined.");
 }

 // this is a problem because height has actually been defined. We can fix this by,
 if (height || height === 0) {
  console.log("Variable is defined.");
 } else {
  console.log("Variable has NOT been defined.");
 }
```

#### Results

> Variable has NOT been defined. (incorrect)
> Variable is defined. (correct)

### Equality operators

In this case == changes the '23' string to 23 and then checks the value

```js
 height = 23;
 if (height == '23') {
  console.log("The == operator does type coercion!\n");
 }
```

This could be an unforeseen error so it is best practice to use strict conversion (===).

### Coding challenge 2

John and Mike both play basketball in different teams. In the latest 3 games.
John's team scored 89, 128, 103 points.
Mike's team scored 116, 94 and 123 points.

1. Calculate the average score for each team.
2. Decide which team wins with the highest average score in the output.
3. Then change the scores to show different winners. Don't forget to take into account that there might be a draw (the same average score).
4. EXTRA: Mary also plays basketball and her team scored 97, 134, and 105 points. Like before log the average winner to the console.
5. Like before, change the scores to generate different winners, keeping in mind there might be draws.

```js
 var johnsAverage = (89 + 128 + 103) / 3;
 var mikesAverage = (116 + 94 + 123) / 3;  
 var marysAverage = (97 + 134 + 105) / 3; 
 
 console.log('John\'s average score: ' + johnsAverage);
 console.log('Mike\'s average score: ' + mikesAverage);
 
 // which is the highest between John and Mike
 if (johnsAverage > mikesAverage) {
  console.log('John has the highest average score: ' + johnsAverage);
 } else if (mikesAverage > johnsAverage) {
  console.log('Mike has the highest average score: ' + mikesAverage);
 } else {
  console.log('Both average scores are the same: ' + johnsAverage);
 }
```

#### Results

> John's average score: 106.66666666666667      
> Mike's average score: 111     
> Mike has the highest average score.

```js
 // Now do checks with Mary's team.
 console.log('John\'s average score: ' + johnsAverage);
 console.log('Mike\'s average score: ' + mikesAverage);
 console.log('Mary\'s average score: ' + marysAverage);
 
 if (johnsAverage > mikesAverage && johnsAverage > marysAverage) {
  console.log('John has the highest average score: ' + johnsAverage);
 } else if (mikesAverage > johnsAverage && mikesAverage > marysAverage) {
  console.log('Mike has the highest average score: ' + mikesAverage);
 } else if (marysAverage > johnsAverage && marysAverage > mikesAverage) {
  console.log('Mary has the highest average score: ' + marysAverage);
 } else {
  console.log('All average scores are the same.');
 }
```

#### Results

> John's average score: 106.66666666666667      
> Mike's average score: 111     
> Mike has the highest average score: 111       
> John's average score: 106.66666666666667      
> Mike's average score: 111     
> Mary's average score: 112     
> Mary has the highest average score: 112

## Functions

```js
 function calculateAge(birthYear) {
  return 2019 - birthYear;
 }
 
 var yearBorn = 1985;
 var firstName = 'Ethan';
 var age = calculateAge(yearBorn);
 console.log('The age is ' + age); // The age is 34
```

.

```js
 function yearsUntilRetirement(year, firstName) {
 
  var age = calculateAge(year); // you can call a function within a function
  var retirement = 65 - age;
 
  if (retirement > 0) {
   console.log(firstName + ' retires in ' + retirement + ' years.');    
  } else {
   console.log(firstName + ' has already retired.');
  }
 }
 
 yearsUntilRetirement(yearBorn, firstName);  // Ethan retires in 31 years.
 
 yearsUntilRetirement(1952, 'Alan');  // Alan has already retired.
```

### Function statements and expressions

```js
 // function expression
 var whatJob = function (job, firstName) {
  
  var output;
  switch (job) {
   case 'teacher':
    output = firstName + ' teaches kids to program.';
    break;
   case 'driver':
    output = firstName + ' drives an uber.';
    break;
   case 'designer':
    output = firstName + ' creates websites.';
    break;
   default:
    output = firstName + ' is retired.';
   }    
 
  return output;
 }

 console.log(whatJob('teacher', 'Joe'));
 console.log(whatJob('designer', 'Mike'));
 console.log(whatJob('driver', 'Mary'));
 console.log(whatJob('retired', 'Alan'));
```

## Arrays

Different ways of creating an array. Arrays are zero based.

```js
 var names = ['john', 'Mark', 'Mary', 'Alan', 'Ethan', 'James', 'Charley'];
 var years = new Array(1960, 1999, 2001, 1952, 1985, 2006, 2011);
 
 console.log(names[0]);
 console.log(names);
 console.log(names.length);
```

#### Results

> john
> [ 'john', 'Mark', 'Mary', 'Alan', 'Ethan', 'James', 'Charley' ]
> 7

**or**

```js
 for (var key in names) {
  console.log(key, names[key]);
 }
```

#### Results

> 0 john        
> 1 Mark        
> 2 Mary        
> 3 Alan        
> 4 Ethan       
> 5 James       
> 6 Charley

**or**

```js
 for(var i = 0; i < names.length; i++){
  console.log(names[i]);
 }
```

#### Results

> john      
> Mark      
> Mary      
> Alan      
> Ethan     
> James     
> Charley       

**or**

```js
 names.forEach(function(element) {
  console.log(element);
 });
```

#### Results

> john      
> Mark      
> Mary      
> Alan      
> Ethan     
> James     
> Charley

### change element in the array

```js
    names[0] = 'Ben';
    console.log();
    names.forEach(function(element) {
     console.log(element);
    });
```

#### Results

> Ben       
> Mark      
> Mary      
> Alan      
> Ethan     
> James     
> Charley

You can even add a value that isn't in the array.

```js
 names[8] = 'Jen';
 console.log('\n' + names + '\n'); // Ben,Mark,Mary,Alan,Ethan,James,Charley,,Jen
 names.forEach(function(element) {
  console.log(element);
 });
```

#### Results

> Ben       
> Mark      
> Mary      
> Alan      
> Ethan     
> James     
> Charley       
> Jen

Different data types in arrays.

```js
 var john = ['John', 'Smith', 1989, 'teacher', false];
 john.push('blue');
 console.log(john); // [ 'John', 'Smith', 1989, 'teacher', false, 'blue' ]

 john.unshift('Mr.'); // add to start of array
 console.log(john); // [ 'Mr.', 'John', 'Smith', 1989, 'teacher', false, 'blue' ]

 john.pop();  // removes last element
 console.log(john); // [ 'Mr.', 'John', 'Smith', 1989, 'teacher', false ]

 john.shift(); // remove first element in array
 console.log(john); // [ 'John', 'Smith', 1989, 'teacher', false ]

 console.log(john.indexOf(1989)); // 2
 console.log(john.indexOf('Alan')); // can't find 'Alan' so returms -1

 var isDesigner = john.indexOf('designer') === -1 ? 'John IS NOT a designer.' : 'John IS a designer.';
 console.log(isDesigner); // John IS NOT a designer.
```

### Coding Challenge 3

John and his family went on a holiday and went to 3 different restaurants. The bills were $124, $48 and $268.

To tip the waiter john created a simple tip calculator (as a function). He likes to tip 20% of the bill when
the bill is less than $50, $15% when the bill is between $50 and $200 and 10% if the bill is more than $200.

In the end John would like to have two arrays:

1. Containing all three tips (one for each bill).
2. Containing all three final paid amounts (bill + tip).

Note: To calculate 20% of a value, simply multiply it with 20/100 = 0.2.

```js
    var header = function() {
     console.log('John\'s tipping program\n');
    };
    
    var printResults =  function(bills) {
    // print out results
    console.log("Tips and Paid Amounts\n");
    for(var j = 0; j < bills.length; j++) {
      console.log('Cost $' + bills[j] + ', tip $' + tips[j].toFixed(2) + '.');
      console.log('Paid amount $' + paidAmounts[j].toFixed(2) + '.');
     }
    };

    var calculator = function(bills) {
     // var tips = [];
     var tip;
     // var paidAmounts = [];
     var paidAmount;
    
     for(var i = 0; i < bills.length; i++) {
      switch (bills[i]) {
       case bills[i] < 50:
        tip = element *0.2;
        break;
       case bills[i] >= 50 && bills[i] < 200:
       tip = bills[i]* 0.15;
        break;
       default:
        tip = bills[i] * 0.1;
      }
      tips.push(tip);
      paidAmount = bills[i] + tips[i];
      paidAmounts.push(paidAmount);
     }
    };

    // global variables
    var tips = [];
    var paidAmounts = [];   
    var bills = [124, 48, 268]; 
    
    header();
    
    calculator(bills);
    
    printResults(bills);
```

#### Results

> John's tipping program        
>       
> Tips and Paid Amounts     
>       
> Cost $124, tip $12.40.        
> Paid amount $136.40.      
> Cost $48, tip $4.80.      
> Paid amount $52.80.       
> Cost $268, tip $26.80.        
> Paid amount $294.80.      

## Objects and properties

Key, value pairs.

```js
    // a better way to make a consistent constructor object
    function Person(firstName, lastName, birthYear, family, job, isMarried) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.birthYear = birthYear;
        this.family = family;
        this.job = job;
        this.isMarried = isMarried;
    }
```

Problem with this is that I haven't figured out how to add a method into the above class.

### Object literal

This is probably the easiest way to create an object.

```js
    var john = {
        firstName: 'John',
        lastName: 'Smith',
        birthYear: 1990,
        family: ['Jane', 'Mark', 'Bob', 'Emily'],
        job: 'teacher',
        isMarried: false
    };

    console.log(john);
    console.log();
    console.log(john.firstName);   // John
    console.log(john['lastName']); // Smith
    
    var x = 'birthYear';
    console.log(x); // 1990
    
    john.job = 'driver';
    console.log(john.job); // driver
    
    john.isMarried = true;
    console.log(john['isMarried']); // true
    console.log();
```
.

```js
 var alan = new Person('Alan', 'Robson', '1952', ['Jen', 'Ethan', 'Justin'], 'Retired', true);

 console.log(alan);
 console.log();
```

### new Object syntax

```js
    var jane = new Object();
    jane.firstName = 'Jane';
    jane.lastName = 'Jones';
    jane.birthYear = 1980;
    jane.family = ['Fred', 'Mary', 'Jill', 'Jana'];
    jane.job = 'nurse';
    jane.isMarried = false; 
    
    console.log(jane);
    console.log();
```

I can add all the objects that I created above into an array and dump them to the console together.

```js
 var people = [john, alan, jane];
 console.log(people);
```

### Objects and methods

This is the easiest way to create a class with a method. The problem is that I can't use it for multiple objects without repeating the method code in each object.

```js
    var john = {
        firstName: 'John',
        lastName: 'Smith',
        birthYear: 1990,
        family: ['Jane', 'Mark', 'Bob', 'Emily'],
        job: 'teacher',
        isMarried: false,
        calcAge: function() {
         this.age = 2019 - this.birthYear;
        }
    };
     
    console.log(john.calcAge()); // 29
```

**Note:**

Originally we set up the function like this.

```js
 calcAge: function(birthYear) {
  return 2019 - this.birthYear;
 }
```

We then had to calculate the age by.

```js
 console.log(john.calcAge(john.birthYear)); // 29
```

Fortunately we can improve this code.

```js
    this.birthYear
```

will get the current birthYear in the Object literal so we don't have to calculate it ourselves.

If we dump the Object with,

```js
    console.log(john);
```

We won't get the calculated age. calcAge will return,

```js
    calcAge: [Function: calcAge]
```

We can work around this by creating a variable in the function.

```js
    calcAge: function(birthYear) {
      this.age = 2019 - this.birthYear;
    }
```

Now we can access the calculated age.

```js
    john.calcAge(); // have to do this
    console.log(john);
```

Also note that we have to run the calcAge function before we can access the .age property.

This is because classes don't actually exist in JavaScript.

#### Results

> undefined     
> { firstName: 'John',      
> lastName: 'Smith',        
> birthYear: 1990,      
> family: [ 'Jane', 'Mark', 'Bob', 'Emily' ],       
> job: 'teacher',       
> isMarried: false,     
> calcAge: [Function: calcAge],     
> age: 29 }

### Coding Challenge 4

Let's remember the first coding challenge where Mark and John compared their BMI's. Let's now implement the same functionality with objects and methods.

1. For each of them, create an object with properties for their full name, mass and height.
2. then, add a method to each object to calculate the BMI. Save the BMI to the Object and also return it from the object.
3. In the end, log to the console who has the highest BMI, together with the full name and the respective BMI. Don't forget that they might have the same BMI.

BMI = mass / height^2 (mass in kg, height in metres).

```js
    var mark =  {
        firstName: 'Mark',
        lastName: 'Smith',
        mass: 78,
        height: 1.69,
        calcBmi: function() {
            this.bmi = this.mass / (this.height * this.height);
     },
     calcName: function() {
        this.fullName = this.firstName + ' ' + this.lastName;
     }
    }; 

    var john =  {
        firstName: 'John',
        lastName: 'Bayley',
        mass: 92,
        height: 1.95,
        calcBmi: function() {
            this.bmi = this.mass / (this.height * this.height);
        },
        calcName: function() {
            this.fullName = this.firstName + ' ' + this.lastName;
        }
    };

    // In JavaScript we have to manually run the methods for each object.
    mark.calcBmi();
    mark.calcName();
    
    // so now we can use the calculated properties
    console.log(mark.fullName + "'s BMI: " + mark.bmi);
    john.calcBmi();
    john.calcName();
    
    console.log(john.fullName + "'s BMI: " + john.bmi);
    
    if (mark.bmi === john.bmi) {
        console.log("Marks's BMI is the same as John's BMI.");
    } else if (mark.bmi > john.bmi) {
        console.log("Marks's BMI is higher than John's BMI.");
    }
    else {
        console.log("Marks's BMI is lower than John's BMI.");
    }
```

#### Results

> Mark Smith's BMI: 27.309968138370508      
> John Bayley's BMI: 24.194608809993426     
> Marks's BMI is higher than John's BMI.

### Loops and iteration

```js
    for (var i = 0; i < 10; i++) {
        console.log(i);
    }
```

.

```js
    var john = ['John', 'Smith', 1990, 'designer', false];

    for (var i = 0; i < john.length; i++) {
        console.log(john[i]);  
    }
```

#### Results

> John      
> Smith     
> 1990      
> designer      
> false

Another variation of looping.

```js
    var i = 0;

    while (i < john.length) {
        console.log(john[i]);  
        i++;
    }
```

### `continue` statement

```js
    var john = ['John', 'Smith', 1990, 'designer', false];
    
    for (var i = 0; i < john.length; i++) {
        if (typeof john[i] !== 'string') {
            continue;
        }

        console.log(john[i]);  
    }
```

I found an unusual instance with the code above. Normally I would wrap  `continue` in *{ continue; }*. This crashes and burns for some reason.

I need to read more about `continue` and `break`.

#### Results

> John      
> Smith     
> designer      

```js
    var john = ['John', 'Smith', 1990, 'designer', false];

    for (var i = 0; i < john.length; i++) {
        if (typeof john[i] !== 'string') {
            break;
        }

        console.log(john[i]);  
    }
```

#### Results

>John       
>Smith


### Coding Challenge 5

Remember the tip calculator challenge? Let's create a more advanced version using everything we learned!

This time, John and his family went to 5 different restaurants. The bills were $124, $48, $268, $180 and $42.
John likes to tip 20% of the bill when the bill is less than $50, 15% when the bill is between $50 and $200, and 10% if the bill is more than $200.

Implement a tip calculator using objects and loops:

1. Create an object with an array for the bill values
2. Add a method to calculate the tip
3. This method should include a loop to iterate over all the paid bills and do the tip calculations
4. As an output, create 1) a new array containing all tips, and 2) an array containing final paid amounts (bill + tip). HINT: Start with two empty arrays [] as properties and then fill them up in the loop.

EXTRA AFTER FINISHING: Mark's family also went on a holiday, going to 4 different restaurants. The bills were $77, $375, $110, and $45.
Mark likes to tip 20% of the bill when the bill is less than $100, 10% when the bill is between $100 and $300, and 25% if the bill is more than $300 (different than John).

5. Implement the same functionality as before, this time using Mark's tipping rules
6. Create a function (not a method) to calculate the average of a given array of tips. HINT: Loop over the array, and in each iteration store the current sum in a variable (starting from 0). After you have the sum of the array, divide it by the number of elements in it (that's how you calculate the average)
7. Calculate the average tip for each family
8. Log to the console which family paid the highest tips on average

.

```js
    var john = {
        fullName: 'John Smith',
        bills: [124, 48, 268, 180, 42],
        calcTips: function() {
         this.tips = [];
         this.finalValues = [];

         for (var i = 0; i < this.bills.length; i++) {
            // Determine percentage based on tipping rules
            var percentage;
            var bill = this.bills[i];

            if (bill < 50) {
                percentage = 0.2;
            } else if (bill >= 50 && bill < 200) {
                percentage = 0.15;
            } else {
                percentage = 0.1;
            }

            // Add results to the corresponding arrays
            this.tips[i] = bill * percentage;
            this.finalValues[i] = bill + bill * percentage;
         }
        }
    };

    var mark = {
        fullName: 'Mark Miller',
        bills: [77, 475, 110, 45],
        calcTips: function() {
            this.tips = [];
            this.finalValues = [];
            
            for (var i = 0; i < this.bills.length; i++) {
                // Determine percentage based on tipping rules
                var percentage;
                var bill = this.bills[i];
                if (bill < 100) {
                 percentage = 0.2;
                } else if (bill >= 100 && bill < 300) {
                 percentage = 0.1;
                } else {
                 percentage = 0.25;
                }
                
                // Add results to the corresponding arrays
                this.tips[i] = bill * percentage;
                this.finalValues[i] = bill + bill * percentage;
            }
        }
    };

    function calcAverage(tips) {
        var sum = 0;

        for (var i = 0; i < tips.length; i++) {
             sum = sum + tips[i];
        }
        
        return sum / tips.length;
    }

    // Do the calculations
    john.calcTips();
    mark.calcTips();
    
    john.average = calcAverage(john.tips);
    mark.average = calcAverage(mark.tips);
    
    console.log(john, mark);
    console.log();
    
    if (john.average > mark.average) {
        console.log(john.fullName + '\'s family pays higher tips, with an average of $' + john.average);
    } else if (mark.average > john.average) {
        console.log(mark.fullName + '\'s family pays higher tips, with an average of $' + mark.average);
    }
```

#### Results

> { fullName: 'John Smith',     
> bills: [ 124, 48, 268, 180, 42 ],     
> calcTips: [Function: calcTips],       
> tips: [ 18.599999999999998, 9.600000000000001, 26.8, 27, 8.4 ],       
> finalValues: [ 142.6, 57.6, 294.8, 207, 50.4 ],       
> average: 18.080000000000002 } { fullName: 'Mark Miller',      
> bills: [ 77, 475, 110, 45 ],      
> calcTips: [Function: calcTips],       
> tips: [ 15.4, 118.75, 11, 9 ],        
> finalValues: [ 92.4, 593.75, 121, 54 ],       
> average: 38.5375 }        
>       
> Mark Miller's family pays higher tips, with an average of $38.5375
