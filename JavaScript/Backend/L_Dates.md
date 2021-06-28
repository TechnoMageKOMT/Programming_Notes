# Dates

## Basics

```JavaScript
  const now = new Date()
  console.log(`Year: ${now.getFullYear()}`)
  console.log(`Month: ${now.getMonth()}`)
  console.log(`Day of a month: ${now.getDate()}`)
  console.log(`Hour: ${now.getHours()}`)
  console.log(`Minutes: ${now.getMinutes()}`)
  console.log(`Seconds: ${now.getSeconds()}`)
```

Dates are stored as numbers based on a starting pooint of 1 January 1970 00:00:00 UTC (UTC = coordinated universal time). This number can, however, be converted to an actual date as follows:

```JavaScript
  const timeStamp = now.getTime()   //This yields the number referred to above
  const actualDate = new Date(timeStamp)
  console.log(actualDate.toString())  //Will give the output of an actual date corresponding to the number
```

This is very limiting in practice, but dates can, for example, be compared to each other:

```JavaScript
  const date1 = new Date(`December 15 2019 0:30:00`)
  const date2 = new Date(`15 December 2020 0:30:00`)
  const timeStampDate1 = date1.getTime()
  const timeStampDate2 = date2.getTime()

  timeStampDate1 < timeStampDate2
    ? console.log(date1.toString())
    : console.log(date2.toString())
  //This code will print whichever date comes first
```

## External library: moment

A far more efficient way of working with dates in JavaScript is by making use of the external library "Moment". Refer: [https://momentjs.com/]. Go to the browser section and click on the cdnjs link. Select version 2.20.1 and make use of the 'moment-with-locales.min.js' script tag. [<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.20.1/moment-with-locales.min.js"></script>]

Refer to the documentation section of the website for information on what methods are available. There is, for example, a section on get & set as well as manipulate (both of which are self explanatory). There is also a display section with options to format the way that dates are displayed.

To get a time stamp using moment:

## Timestamp using moment

```JavaScript
  const timestamp = moment().valueOf()
```
