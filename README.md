### Haskell 101 - Study log

#### Setup

```sh
sudo apt-get install haskell-platform

// After completion, run `ghci` to check if everything works

ghci

// To exit `ghci`, type
:quit exit
```

#### Basic data models

**Numbers** are kinda obvious:

```sh
Prelude> 1 + 1

// Output: 2
```

**Chars** can use single or double quotation, while **Strings** have to use double quotation:

> Hint: use `:t` to check the inferred input type

```sh
Prelude> :t "X" // or :t 'X'

// Output: "X" :: [Char]

Prelude> :t "Lorem Ipsum"

// Output: "Lorem Ipsum" :: [Char]
```

> You can even use _ASCII_ to represent something. I don't know (at least, at this point) why anyone would do that, but is good to have this feature.

**Booleans** are the same as any other language, the only difference (from the languages I used) is that you use it capitalized:

```sh
Prelude> True

// Output: True

Prelude> False

// Output: False
```

**Lists** can only contain items with the same type:

```sh
Prelude> [a,b,c]

// Output: [a,b,c]

Prelude> [a,b,c,1]

// Output: Error
```

You can even generate a list (which is called _list comprehension_) using math:

```sh
// Notation: [output | range, condition]

Prelude> [x*2| x<-[1..3]]

// Input: Create a list from another list ([1, 2, 3]), where each entry should be multiplied by 2

// Output: [2,4,6]
```

> Lists can be mutated at runtime

**Tuples** are immutable lists which can have basically anything you want inside it:

```sh
Prelude> (0,1,"X","Lorem Ipsum")

// Output: (0,1,"X","Lorem Ipsum")
```

##### Basic operators

They are the same as any other language:

```
+ -> add
- -> subtract
* -> multiply
/ -> divide
```

We can count as a basic operator the **Range operator**. We already used it on the _list comprehension_ above:

```
Input: [0..5]

Output: [0,1,2,3,4,5]
```

#### Conditions

The example above will test if `x` is an _even_ or _odd_ number and print the output:

```haskell
main = do
  let x = 5

  if x `rem` 2 == 0
    then putStrLn "Even"
  else putStrLn "Odd"
```

You can nest if/else blocks too, but why someone would do this kind of atrocity? Keep stuff simple pls.

#### Basic types

- **Int** -> Anything between `2147483647` and `-2147483647`

- **Integer** -> Basically an `Int` on steroids. You can use your `2147483648` and it won't throw an error.

- **Float** -> `1.1`, `2.2`, etc. You get it.

- **Double** -> Floating point with double precision. Is like a float with an sniper's scope attached.

- **Bool** -> `True`. Or `False`.

- **Char** -> Anything quoted. Like `'this'`.

- **EQ** -> Compare equality (or not) with `==` and `/=`

- **Ord** -> Ordering. Options are `>`, `<`, `<=`, `>=` and `compare`

- **Show** -> Transform any given argument into string, e.g.:

```haskell
main = print (show 123) // 123 -> number

// Output: "123"
```

- **Read** -> Transform any given argument into another type, e.g.:

```haskell
main = print (readInt "123") // "123" -> string

// Output: 123
```

- **Enum** -> Here is where things became weird. This thing can be accessed with `succ`, `pred`, etc. Probably I'll see more about it in the future:

```haskell
// succ = Successor
// pred = Predecessor
// There are more enums, but whatever for now

main = print (pred 123) // get the predecessor of 123

// Output: 122

main = print (pred 122) // get the successor of 122

// Output: 123
```

- **Bounded** -> I think it sets `min` and `max` values for something, like another type using `minBound` and `maxBound`, idk

- **Num** -> Any kind of numeric operations

- **Integral** -> Subset of `Num` for `Int` and `Integer` operations

- **Floating** -> Subset of `Num` for `Float` and `Double` operations
