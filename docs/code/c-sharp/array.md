# Array
```cs
// Fixed size array
T[] array = new T[size];
```

## Fill With Constant
> [!NOTE]
> Unlike C/C++, C# sets a default value on primitive types (eg: int[] -> everything is set to 0 by default)

```cs
Array.Fill(array, value);
```

## Sort One Array Based on Another
```cs
int[] x = [3, 2, 1];
int[] y = [0, 10, 100];

Array.Sort(x, y);
// x = [1, 2, 3]
// y = [100, 10, 0]
```
