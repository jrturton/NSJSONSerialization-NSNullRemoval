[![Build Status](https://travis-ci.org/jrturton/NSJSONSerialization-NSNullRemoval.svg)](https://travis-ci.org/jrturton/NSJSONSerialization-NSNullRemoval)

NSJSONSerialization-NSNullRemoval
=================================

Categories on NSJSONSerialization, NSMutableDictionary and NSMutableArray to recursively remove NSNull objects often returned from JSON web services. 

To directly remove from a JSON web response:

```objc
stripped = [NSJSONSerialization JSONObjectWithData:data options:NSJSONReadingMutableContainers error:nil removingNulls:YES ignoreArrays:NO];
```

The `ignoreArrays` parameter will leave `NSNull` objects contained directly within arrays in place, for situations when the count of the returned array is important. 

`NSJSONReadingMutableContainers` will be force added to the options if it is not present, since the null removal depends on it.

Methods are also available to recursively remove NSNull objects from dictionaries and arrays, if preferred:
```objc
[mutableArray recursivelyRemoveNulls];
```
or
```objc
[mutableArray recursivelyRemoveNullsIgnoringArrays:YES];
```
