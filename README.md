# Swift Styles

I'm reading [Erica Sadun](https://github.com/erica)'s Swift Style and rethinking the way I'm structuring my code. This is an ongoing project, so it might be often changed.

## Code

### limits

| type | limit |
|:-:|:-:|
| function | 40 rows |
| function | 5 parameters |
| file | 400 rows |
| file | 120 columns |

### tab or not to tab
Use tabs

### assignment

Add type only if it's explicitly required by the compiler.

```swift 
let value = 2
let key = 3
let optional: String?
```

Do not coalign assignments, because if a longer variable is added to that block, then every other one needs to be realigned making an unnecessary maintenance.

```swift 
let yes = true
let no  = false
let maybe = false // longer var
```

### enum

Add `enum` options line by line.

```swift
enum State {

    case
    blah,
    bleh

}
```

### if else

Colinear braces only if it's a simple action.

```swift 
if value > key { /* ...do something */ }
```

Use 1TBS bracing.

```swift 
if value == key {
    // ...do something
} else if value > key {
    // ...do something
} else if
    value < key,
    key != 2 {
    // ...do something else
} else {
    
    // ...do something else
    // ...do something else

}
```

### do catch

`do catch` must be placed as following:

```swift
do {
    // ...try something
} catch {
    // ...catch something
}
```

### switch case

Cases together. If cases have the same value, add them line by line. Single line only if it's a single action:

```swift
switch self {
    case .default: return
    case .other:
        // ...do something 
        return
    case .onevalue,
         .sameOneValue: return
}
```

### guard

Add each guard conditional statement in a new line and wrap `return` in the same line of `else` or in the same line **as long as the code does not turn out hard to read**.

```swift 
guard
    let opt = optional
    else { return }
    
guard let opt = optional else { return }    
```

If you want to add more code inside `else`, then add it in a new line and make braces more spaced.

```swift 
guard
    let opt = optional,
    key == true
    else {
        
        // ...do something
        return
        
}
```

### functions

Colinear braces only if it's a simple action or empty initializer.

```swift 
init() { }
func first() { /* do something */ }
```

If the function has more than one action or non-empty initializer, then add a new line before and after the code block.

```swift 
init() {

    // ...do something
    
}

func second() {
    
    // ...do something
    // ...do something else
    
}
```

When you have a single argument, then add it in the same line of the function. "Braces want to breathe, parentheses want to hug" (Erica Sadun - Swift Styles).

```swift 
func third(one: String) {
    
}
```

When you have more than one argument, add it one line below. This way makes both paramenters in the same column and allows us to debug every parameter separately.

```swift 
public func fourth(one: String,
                   second: String) {
    
}
```

When calling the function, call them in the same line **as long as the code does not turn out hard to read**.

```swift
fourth(one: "", second: "")

fourth(one: "", 
       second: "")
```

Add the return type in the same line of the last parentheses.

```swift 
public func fifth(one: String,
                  second: String) -> Int {
    
    return 2
    
}

let a = fifth(one: "",
              second: "")
```

When you have a `where` clause, add it one line below of the closing parentheses.

```swift 
func sixth<C>(one: String,
           two: String,
           third: C) -> Int
    where C: Collection, C.Iterator.Element == Character {
        
        return 2
        
}

let b = sixth(one: "",
              two: "",
              third: [""])
```

#### spaces around function parentheses

Do not add them.

```swift 
print( "a", "x" )
```

#### chaining functions

When chaining functions add the first one in the first line and the other on each line below. Make them breathe though.

```swift
let threes = (1...15)
    .filter({
        $0 % 3 == 0
    })
    .map({
        "#\($0)"
    })

print(threes)
```

### closure

Make closure as clean as possible.

Instead of doing this:

```swift
{ (index: Index) -> Void in
}
```

Do this:

```swift
{ index in // way much cleaner
}
```

### shorthand arguments

Limit the use shorthand arguments (`$0`, `$1`, `...`) for simplest closures, such as those used when mapping, filtering and sorting.

```swift
[(0, 1), (3, 2)].map({ $0 < $1 }) // avoid
[(0, 1), (3, 2)].map(<) // do it
```

## File structure

### MVVM
// TODO


## Folder structure

### View Controler
// TODO

### View Models
// TODO

### Extensions
// TODO

### Views
// TODO