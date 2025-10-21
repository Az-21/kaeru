# C#
## Array
```cs
// Fixed size array
T[] array = new T[size];
```

### Fill With Constant
!!! note
    Unlike C/C++, C# sets a default value on primitive types (eg: int[] -> everything is set to 0 by default)

```cs
Array.Fill(array, value);
```

### Sort One Array Based on Another
```cs
int[] x = [3, 2, 1];
int[] y = [0, 10, 100];

Array.Sort(x, y);
// x = [1, 2, 3]
// y = [100, 10, 0]
```

## Dictionary (HashMap)
```cs
using System.Collections.Generic;
```

```cs
// Initialize
Dictionary<KeyType, ValueType> hashmap = [];

// Add key value pair
hashmap.TryAdd(key, value);

// Discard key value pair
hashmap.Remove(key, out T value) // Optional overload to capture value

// Check if key exists in dictionary
hashmap.ContainsKey(key)

// Get value associated with a key
hashmap.TryGetValue(key, out T value)

// Iterate over key value pairs
foreach(KeyValuePair<T1, T2> kvp in hashmap) {
  Console.WriteLine($"{kvp.key}: {kvp.value}");
}

// Separate iterable collection of keys and values
ICollection<KeyType> = hashmap.Keys;
ICollection<ValueType> = hashmap.Values;
```

### Obtain Maximum/Minimum
```cs
var maxKvpByKey   = hashmap.MaxBy(kvp => kvp.Key);
var maxKvpByValue = hashmap.MaxBy(kvp => kvp.Value);

var minKvpByKey   = hashmap.MinBy(kvp => kvp.Key);
var minKvpByValue = hashmap.MinBy(kvp => kvp.Value);
```

### Using `bool` Output of Operations
Operations like `TryAdd` emit a `bool` success output. It can be optionally captured to check if the operation was completed.
```cs
bool success = hashmap.TryAdd(x, 1);
if(!success) { hashmap[x]++; }
```
