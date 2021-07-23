# The Rest Parameter

This is a way of taking in arguments to a function when the exact number of the arguments are not know.

The rest operator (...) will then take in the multiple arguments as an array.

```JavaScript
const printTeam = (team, coach, ...players) => {
  console.log(`Team: ${team}`)
  console.log(`Coach: ${coach}`)
  console.log(`Players: ${players.join(', ')} `)
}

printTeam('Sparrows', 'John Smith', 'Mary', 'Andrew', 'Kim')
```
