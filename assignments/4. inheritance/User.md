# Inheritance

User
  -properties
    -name
    -score
  -methods
    -increaseScore: returns score increased by 1
    -decreaseScore: returna score decreased by 1

PaidUser
  -properties
    -name
    -score
    -balance
  -methods
    -increaseScroe: returns score increased by 1
    -decreaseScore: returna score decreased by 1
    -increaseBalance: returna balance decreased by 1

Using Inheritance convert the above into following patterns.

1. Prototypal Pattern
2. Pseudoclassical Pattern
3. Classes

<!-- 1. prototypal pattern -->

```js
var userMethod = {
  increaseScore: function() { return this.score ++;},
  decreaseScore: function() { return this.score --;}
}

function User(name, score = 1) {
  var user = Object.create(userMethod);
  user.name = name;
  user.score = score;
  return user;
}

var paidMethod = {
  increaseBalance: function() { return this.balance ++;}
}

function paidUser(name, score = 1, balance = 1) {
  var user = User(name, score);
  Object.setPrototypeOf(user, userMethod);
  Object.setPrototypeOf(userMethod, paidMethod);
  user.balance = balance;
  return user;
}

var ishav = paidUser("ishav");

ishav
// output name: "ishav", score: 1, balance: 1}


```