# EasyLang VSCode Extension

Basic language support for **EasyLang**:

> [!TIP]
> This extension can be downloaded from the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=Greenbugx0xNA.easylang) or installed directly within VS Code by searching for "EasyLang".

## Features

### Syntax Highlighting

EasyLang's VS Code extension provides comprehensive syntax highlighting driven by a TextMate grammar (v0.1.3) that recognizes all major language constructs:

- **Control Flow**: `if`, `then`, `else`, `repeat`, `while`, `from`, `to`, `do`, `continue`, `break`, `return`, `try`, `handle`
- **Declarations**: `let`, `constant`, `be` (reassignment), `=` (assignment), `define`
- **Pattern Matching**: `match`, `when`, `otherwise`, `with`
- **Logical Operators**: `and`, `or`, `not`, `equals`, `not equals`
- **Comparison**: `less`, `greater` (word-based), `==`, `!=`, `<`, `>`, `<=`, `>=` (symbol-based)
- **Arithmetic**: Word-based (`plus`, `minus`, `mul`, `div`, `modulus`, `expo`) and symbol-based (`+`, `-`, `*`, `/`, `%`, `**`, `//`)
- **Type Keywords**: `int`, `float`, `text`, `boolean`
- **Comments**: Single-line (`$`) and block (`$$ ... $$`) comments
- **Strings & Numbers**: Double-quoted strings with escape sequences, integers and floats
- **Object-Oriented**: `define class`, `define method`, `make`, `self` keyword
- **Module System**: `bring`, `as` (for imports)
- **File I/O**: `print`, `read`, `open`, `close`, `readline`, `writeline`, `as`, `for`, `into`, `with`
- **Collections**: Dictionary literals with `{ key: value }` syntax

### File Association

Automatically recognizes and opens `.elang` and `.elangh` files with EasyLang syntax highlighting enabled.

## Installation

Install the EasyLang extension from the [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=Greenbugx0xNA.easylang), or launch VS Code Quick Open (`Ctrl+P`) and paste:

```
ext install Greenbugx0xNA.easylang
```

Then open or create files with `.elang` or `.elangh` extensions to get instant EasyLang-aware syntax highlighting.

## Customization

Combine this extension with your preferred VS Code theme to fine-tune the colors applied to the EasyLang TextMate scopes. Different themes will render syntax tokens with varying color schemes. The grammar file `easylang.tmLanguage.json` defines all scope names for theme customization.

## Supported Language Constructs

### Comments

```easylang
$ This is a line comment

$$ This is a
   block comment
   spanning multiple lines
$$
```

### Data Types

```easylang
let count be 5              $ integer
let pi be 3.14159          $ float
let name be "Alice"        $ text/string
let active be true         $ boolean
let empty be null          $ null value
```

### Variable Declaration & Assignment

```easylang
let x = 10                 $ initialization with =
constant TIMEOUT = 5       $ immutable constant
x be 20                    $ reassignment with be
```

### Control Flow - Conditionals

Control flow uses bracket-based blocks `[ ... ]` instead of `end` keywords:

```easylang
if score greater 90 then [
    print "Excellent!"
] else if score greater 80 then [
    print "Good!"
] else [
    print "Keep trying"
]
```

### Control Flow - Loops

```easylang
$ Counted loop
repeat from i = 1 to 5: do [
    print i
]

$ While loop
repeat while counter greater 0: do [
    print counter
    counter be counter minus 1
]

$ ForEach loop
repeat item from myList: do [
    print item
]
```

### Functions & Methods

```easylang
$ Free function with parameters
define add(x, y): do [
    return x plus y
]

$ Free function without parameters
define greet(): do [
    print "Hello!"
]

$ Class definition with methods
define class Person: [
    let name be "Unknown"
    let age be 0

    define method when_created(n, a): do [
        self.name be n
        self.age be a
    ]

    define method introduce(): do [
        print "I am " plus self.name
    ]
]

$ Create instance
make person1 be Person("Alice", 25)
person1.introduce()
```

### Pattern Matching

```easylang
match day with [
    when "Monday" then [
        print "Start of week"
    ]
    when "Friday" or "Saturday" or "Sunday" then [
        print "Near weekend"
    ]
    otherwise [
        print "Midweek day"
    ]
]
```

### Collections

#### Arrays/Lists

```easylang
let numbers be [1, 2, 3, 4, 5]
print numbers[0]           $ access element
numbers.push(6)            $ add element
numbers.pop()              $ remove last element
print numbers.length()     $ get size
```

#### Dictionaries/Objects

```easylang
let user be { name: "Bob", age: 30, active: true }
print user["name"]         $ access by key
user["email"] be "bob@example.com"  $ add/update key
print user.keys()          $ get all keys
print user.values()        $ get all values
```

### Input/Output

```easylang
print "Hello, World!"
read userInput

$ File operations
open "data.txt" as file for read
readline file into line
print line
close file

open "output.txt" as out for write
writeline out with "Result: 42"
close out
```

### Error Handling

```easylang
try [
    let result be 10 div 0  $ might fail
] handle error [
    print "Error occurred!"
]
```

### Modules & Imports

```easylang
bring "strings" as str
bring "math.elangh"
bring "time" as t

print str.upper("hello")
print math.sqrt(16)
```

## Operators Reference

### Arithmetic (Word-Based)

```easylang
5 plus 3        $ 8
10 minus 4      $ 6
3 mul 4         $ 12
20 div 5        $ 4.0
10 modulus 3    $ 1
2 expo 3        $ 8
```

### Arithmetic (Symbol-Based)

```easylang
5 + 3           $ 8
10 - 4          $ 6
3 * 4           $ 12
20 / 5          $ 4.0
10 % 3          $ 1
2 ** 3          $ 8 (power)
10 // 3         $ 3 (integer division)
```

### Comparison (Word-Based)

```easylang
x less y
x greater y
x equals y
```

### Comparison (Symbol-Based)

```easylang
x == y
x != y
x < y
x > y
x <= y
x >= y
```

### Logical

```easylang
true and false  $ false
true or false   $ true
not true        $ false
```

### Assignment

```easylang
let x = 5       $ initialization
x be 10         $ reassignment
x += 5          $ compound assignment (add)
x -= 2          $ compound assignment (subtract)
x *= 3          $ compound assignment (multiply)
x /= 2          $ compound assignment (divide)
```

## TextMate Grammar Details

The extension uses a comprehensive TextMate grammar (`easylang.tmLanguage.json`) that defines tokenization rules for all EasyLang language features. The grammar includes:

- **Scope categories**: 15+ distinct pattern groups for precise highlighting
- **Bracket-based blocks**: Full support for `[ ]` delimited code blocks
- **Dictionary literals**: Special handling for `{ key: value }` syntax
- **Module system**: Recognition of `bring` imports and `as` aliases
- **Operator separation**: Distinct scopes for arithmetic, comparison, and logical operators
- **Word operators**: Dedicated patterns for English-like operators

This ensures consistent and accurate syntax highlighting across different color themes in VS Code.

## Example Programs

### Hello World

```easylang
print "Hello, World!"
```

### Factorial Function

```easylang
define factorial(n): do [
    if n less 2 then [
        return 1
    ]
    return n mul factorial(n minus 1)
]

print factorial(5)  $ Output: 120
```

### Working with Data

```easylang
bring "strings" as str

let users be [
    { name: "Alice", score: 95 },
    { name: "Bob", score: 87 },
    { name: "Charlie", score: 92 }
]

repeat user from users: do [
    let status be "Pass"
    if user["score"] less 90 then [
        status be "Review"
    ]
    print str.upper(user["name"]) plus ": " plus status
]
```

## Requirements

- Visual Studio Code v1.80.0 or later
- EasyLang 0.1.2 or compatible versions

## Support

For issues, feature requests, or contributions, visit the [GitHub repository](https://github.com/greenbugx/ELANG-Extension).

## License

This extension is released under the MIT License. See LICENSE file for details.

## Changelog

### Version 0.1.5

- Updated TextMate grammar (v013) with enhanced operator support
- Added dictionary literal syntax highlighting
- Improved module import keyword recognition
- Fixed integer division operator patterns
- Separated comparison and arithmetic operator scopes
- Added `define` keyword highlighting
- Enhanced file I/O keyword modifiers
