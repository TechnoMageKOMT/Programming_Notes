# Dictionaries

## Definition

Unordered mappings for storing objects as oposed to ordered lists. Dictionaries use a key:value pairing to stored data. This allows quick access to data without knowing an index number (position) of an element.

## Syntax

```Python
dictionary_name = {'key1': 'value1', 'key2': 'value'}
#Retrieving a value
dictionary_name['key1']
#Appending a new entry
dictionary_name['newKey'] = newValue
#This can also be used to overwrite an existing value.
```

## Dictionaries versus Lists

Dictionaries: Objects retrieved by key name. They are unordered and cannot be sorted.

Lists: Objects are retrieved by location. They are ordered sequences that can be indexed or sliced.

## .keys() method

Returns all the keys in a dictionary: `dictionary_name.keys()`

## .values() method

Returns all the values in a dictionary: `dictionary_name.values()`

## .items() method

Returns all the key:value pairs: `dictionary_name.items()`

