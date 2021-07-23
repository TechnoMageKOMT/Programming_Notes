# The Spread Syntax

The spread operator is the opposite of the rest parameter.

```JavaScript
const printTeam = (team, coach, player1, player2, player3) => {
  console.log(`Team: ${team}`)
  console.log(`Coach: ${coach}`)
  console.log(`Players: ${player1}, ${player2}, ${player3}`)
}

const team = {
  name: 'Sparrows',
  coach: 'John Smith',
  players: ['Mary', 'Andrew', 'Kim'],
}

printTeam(team.name, team.coach, ...team.players)
```

It can also be used together with the rest operator as follows:

```JavaScript
const printTeam = (team, coach, ...players) => {
  console.log(`Team: ${team}`)
  console.log(`Coach: ${coach}`)
  console.log(`Players: ${players.join(', ')}`)
}

const team = {
  name: 'Sparrows',
  coach: 'John Smith',
  players: ['Mary', 'Andrew', 'Kim'],
}

printTeam(team.name, team.coach, ...team.players)
```

## Cloning an array

```JavaScript
const cities = ['Barcelona', 'Cape Town', 'Bordeaux']
const citiesClone = [...cities]
```

Once an array has been cloned in this way, any changes to either of the two arrays will **not** affect the other.

The contents of an array can also be copied together with any new content as follow:

```JavaScript
const cities = ['Barcelona', 'Cape Town', 'Bordeaux']
const citiesClone = ['Santiago', ...cities]
```

The spread operator does not have to be last it can also be at the beginning.

## Alternative method to add items to an array

Instead of adding to the cities array using push() for example. The spread operator can be used:

```JavaScript
cities = [...cities, 'newCity']
// or
cities = ['newCity', ...cities]
```

## The Object Spread Syntax

```JavaScript
let house = {
  bedrooms: 2,
  bathrooms: 1.5,
  yearBuilt: 2017,
}

let newHouse = {
  ...house,
}

console.log(house)
console.log(newHouse)
```

Any changes made to one of the objects will now not affect the other.

Just like with arrays, new items can be added to the new object at the same time.

The value of one of the original properties can also be overridden as follow:

```JavaScript
let house = {
  bedrooms: 2,
  bathrooms: 1.5,
  yearBuilt: 2017,
}

let newHouse = {
  ...house,
  bedrooms: 3
}

console.log(house)
console.log(newHouse)
```

**NB** The order is important here. The value change must take place after the spread operation.

Two objects can also be merged using the spread operator:

```JavaSCript
const person = {
  name: 'Johann',
  age: 46,
}

const location = {
  city: 'Kempton Park',
  country: 'South Africa',
}

const overview = {
  ...person,
  ...location,
}

console.log(overview)
```
