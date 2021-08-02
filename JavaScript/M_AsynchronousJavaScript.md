# Asynchronous JavaScript

## Making an HTTP request

```JavaScript
const request = new XMLHttpRequest()
```

The `XML` in the name of the constructor function is not relevant anymore. I.e., We are not dealing with the XML format, but with JSON instead. The name is historical.

The first step is to specify the relevant URL and the http method (GET or POST)

```JavaScript
const request = new XMLHttpRequest()

request.open('GET', 'someURL')
```

Next the request must be sent or initiated as follows. This process does not take place right away. It takes time to connect with the server, some time for the server to process the request and some time for the information to be sent back.

```JavaScript
const request = new XMLHttpRequest()

request.open('GET', 'someURL')
request.send()
```

Next an event listener is set up on request to listen for 'readystatechange' events. refer:[https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/readyState] for information on the four different states. The only state that we will ever be responding to is 4 (DONE - The operation is complete).

```JavaScript
const request = new XMLHttpRequest()

request.addEventListener('readystatechange', (e) => {
  if (e.target.readyState === 4) {
    console.log(e.target)

  }
})
request.open('GET', 'someURL')
request.send()
```

The next step is to access the responseText property on e.target to obtain the JSON data:

```JavaScript
const request = new XMLHttpRequest()

request.addEventListener('readystatechange', (e) => {
  if (e.target.readyState === 4) {
    const data = JSON.parse(e.target.responseText)
    console.log(data)
  }
})
request.open('GET', 'someURL')
request.send()
```

The next step might be to add some more logic to handle http status codes to check if the request was succesfull:

```JavaScript
const request = new XMLHttpRequest()

request.addEventListener('readystatechange', (e) => {
  if (e.target.readyState === 4 && e.target.status === 200) {
    const data = JSON.parse(e.target.responseText)
    console.log(data)
  } else if (e.target.readyState === 4) {
    console.log('An error has taken place')
  }
})

request.open('GET', 'someURL')
request.send()
```

Some useful resources:

http: status codes: [httpstatuses.com]
MDN Http messages: [https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages]

## Asynchronous excecution

Add third argument to `request.open`. `true` is for asynchronous and is the default.

Asynchronous sometimes referred to as non-blocking code and synchronous as blocking code.

```JavaScript
getPuzzle((error, puzzle) => {
  if (error) {
    console.log(`Error: ${error}`)
  } else {
    console.log(puzzle)
  }
})

const getPuzzle = (callback) => {
  const request = new XMLHttpRequest()
  request.addEventListener('readystatechange', (e) => {
    if (e.target.readyState === 4 && e.target.status === 200) {
      const data = JSON.parse(e.target.responseText)
      callback(undefined, data.puzzle)
    } else if (e.target.readyState === 4) {
      callback('An error has occurred', undefined)
    }
  })
  request.open('GET', 'someURLThatReturnRandomWordsForPuzzleGame')
  request.send()
}
```

```JavaScript
getCountryDetails('ZA', (error, country) => {
  if (error) {
    console.log(`Error: ${error}`)
  } else {
    console.log(country.name)
  }
})

const getCountryDetails = (countryCode, callback) => {
  const countryRequest = new XMLHttpRequest()

  countryRequest.open('GET', 'countryDataBaseAPI')
  countryRequest.send()

  countryRequest.addEventListener('readystatechange', (e) => {
    if (e.target.readyState === 4 && e.target.status === 200) {
      const data = JSON.parse(e.target.responseText)
      const country = data.find((country) => country.alpha2Code === countryCode)
      callback(undefined, country)
    } else if (e.target.readyState === 4) {
      callback('An error has occurred', undefined)
    }
  })
}
```

## Closures

```JavaScript
const createCounter = () => {
  let count = 0

  return {
    increment() {
      count++
    },
    decrement() {
      count--
    },
    get() {
      return count
    },
  }
}

const counter = createCounter()
counter.increment()
counter.decrement()
counter.decrement()
console.log(counter.get())
```

## Promises

Using the asynchronous example. A solution by using a promise would look as follow:

```JavaScript
const getPuzzle = (wordCount) =>
  new Promise((resolve, reject) => {
    const request = new XMLHttpRequest()
    request.addEventListener('readystatechange', (e) => {
      if (e.target.readyState === 4 && e.target.status === 200) {
        const data = JSON.parse(e.target.responseText)
        resolve(data.puzzle)
      } else if (e.target.readyState === 4) {
        reject('An error has taken place')
      }
    })
    request.open('GET', `URLPuzzleAPI${wordCount}`)
    request.send()
  })


getPuzzle('2').then(
  (puzzle) => {
    console.log(puzzle)
  },
  (err) => {
    console.log(`Error: ${err}`)
  }
)
```

Using the second asynchronous example:

```JavaScript
const getCountryDetails = (countryCode) =>
  new Promise((resolve, reject) => {
    const countryRequest = new XMLHttpRequest()

    countryRequest.open('GET', 'countryDataBaseAPIURL')
    countryRequest.send()

    countryRequest.addEventListener('readystatechange', (e) => {
      if (e.target.readyState === 4 && e.target.status === 200) {
        const data = JSON.parse(e.target.responseText)
        const country = data.find(
          (country) => country.alpha2Code === countryCode
        )
        resolve(country)
      } else if (e.target.readyState === 4) {
        reject('An error has occurred!')
      }
    })
  })

getCountryDetails('ZA').then(
  (country) => {
    console.log(country.name)
  },
  (err) => {
    console.log(`Error: ${err}`)
  }
)
```

A more concise example:

```JavaScript
let p = new Promise((resolve, reject) => {
  let a = 1 + 1
  if (a === 2) {
    resolve('Success)
  } else {
    reject('Failed)
  }
})

p.then((message) => {
  console.log(`This is in the then: ${message}`)
}).catch((message) => {
  console.log(`This is in the catch: ${message}`)
})
```

## Chaining promises

Should the same asynchronous function need to be run multiple times:

```JavaScript
const getDataPromise = (num) =>
  new Promise((resolve, reject) => {
    setTimeout(() => {
      typeof num === 'number'
        ? resolve(num * 2)
        : reject('Please provide a number')
    }, 2000)
  })

getDataPromise(10)
  .then((data) => {
    return getDataPromise(data)
  })
  .then((data) => {
    return getDataPromise(data)
  })
  .then((data) => {
    console.log(data)
  })
  .catch((err) => {
    console.log(err)
  })
```

## Multiple promises

```JavaScript
const recordVideoOne = new Promise((resolve, reject) => {
  resolve('Video 1 recorded)
})
const recordVideoTwo = new Promise((resolve, reject) => {
  resolve('Video 1 recorded)
})
const recordVideoThree = new Promise((resolve, reject) => {
  resolve('Video 1 recorded)
})

Promise.all([
  recordVideoOne,
  recordVideoTwo,
  recordVideoThree,
]).then((message) => {
  console.log(message)
})
```

`.then()` here will return an array with all of the resolve messages.

`Promise.race()` does the same thing, but it will return as soon as the first promise comes back and will therefore return a single resolve message.

## Fetch API

Using the 'puzzle' example above again, a fetch request will achieve the above in a much simpler way:

```JavaScript
const getPuzzle = (wordCount) => {
  return fetch(`URLPuzzleAPI${wordCount}`)
    .then((response) => {
      if (response.status === 200) {
        return response.json()
      } else {
        throw new Error('Unable to fetch puzzle')
      }
    })
    .then((data) => {
      return data.puzzle
    })
}

getPuzzle('2')
  .then((puzzle) => {
    console.log(puzzle)
  })
  .catch((err) => {
    console.log(`Error: ${err}`)
  })
```

```JavaScript
const getCountryDetails = (countryCode) => {
  return fetch('countryDataBaseAPIURL')
    .then((response) => {
      if (response.status === 200) {
        return response.json()
      } else {
        throw new Error('Unable to fetch data')
      }
    })
    .then((data) => {
      return (country = data.find(
        (country) => country.alpha2Code === countryCode
      ))
    })
}

getCountryDetails('ZA')
  .then((country) => {
    console.log(country.name)
  })
  .catch((err) => {
    console.log(`Error: ${err}`)
  })
```

## Async-await

The tools we have to work with here is the `async` function and the `await` operator.

An "async" function (see below) always returns a promise:

```JavaScript
const asyncFunction = async () => {

}
console.log(asyncFunction())
//Output: Promise { undefined }
```

Converting the 'puzzle examples above to async-await:

```JavaScript
const getPuzzle = async (wordCount) => {
  const response = await fetch(
    `URLPuzzleAPI${wordCount}`
  )

  if (response.status === 200) {
    const data = await response.json()
    return data.puzzle
  } else {
    throw new Error('Unable to get puzzle')
  }
}

getPuzzle('2')
  .then((puzzle) => {
    console.log(puzzle)
  })
  .catch((err) => {
    console.log(`Error: ${err}`)
  })
```
