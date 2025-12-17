# EasyLang VSCode Extension

Basic language support for **EasyLang**:

> [TIP] This extension can be downloaded from the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=Greenbugx0xNA.easylang) or installed directly within VS Code by searching for "EasyLang".

## Features

**Syntax Highlighting**

EasyLang's VS Code extension provides comprehensive syntax highlighting driven by a TextMate grammar that recognizes all major language constructs:

- **Control Flow**: `if`, `then`, `else`, `repeat`, `while`, `from`, `to`, `continue`, `break`, `return`, `try`, `handle`
- **Declarations**: `let`, `constant`, `so`, `be`
- **Pattern Matching**: `match`, `when`, `otherwise`, `with`
- **Logical Operators**: `and`, `or`, `not`, `equals`, `not equals`
- **Type Keywords**: `int`, `float`, `text`, `boolean`
- **Operators**: Word-based (`plus`, `minus`, `mul`, `div`, `modulus`, `expo`) and symbol-based (`+`, `-`, `*`, `/`, `%`, `**`, `//`, `==`, `!=`, `<=`, `>=`, `<`, `>`, `:`)
- **Comments**: Single-line (`$`) and block (`$$ ... $$`) comments
- **Strings & Numbers**: Double-quoted strings with escape sequences, integers and floats
- **Object-Oriented**: `define class`, `define method`, `make`, `class`, and `self` keyword

**File Association**

Automatically recognizes and opens `.elang` and `.elangh` files with EasyLang syntax highlighting enabled.

## Installation

Install the EasyLang extension from the VS Code Marketplace, then open or create files with `.elang` or `.elangh` extensions to get instant EasyLang-aware syntax highlighting.

## Customization

Combine this extension with your preferred VS Code theme to fine-tune the colors applied to the EasyLang TextMate scopes defined in `easylang.tmLanguage.json`. Different themes will render the syntax tokens with varying color schemes based on their configuration.

## Supported Constructs

### Comments
- **Line comments**: `$ This is a comment`
- **Block comments**: `$$ Multi-line comment $$`

### Data Types
- **Primitives**: `int`, `float`, `text`, `boolean`
- **Special values**: `true`, `false`, `null`

### Declarations & Assignment
```
let name be value
constant PI be 3.14159
let x so value
```

### Control Flow
```
if condition then
  $ do something
else
  $ do something else
end

repeat 5 times do
  $ code here
end

while condition do
  $ code here
end

from 1 to 10 do
  $ code here
end
```

### Functions & Methods
```
define myFunction(param1, param2): do
  return param1 plus param2
end

define class MyClass [
  define method getData(): do
    return self.data
  end
]
```

### Pattern Matching
```
match value with
  when 1 then print "one"
  when 2 then print "two"
  otherwise print "other"
end
```

### Input/Output
```
print "Hello, World!"
read variable
open file as handle
close handle
readline from handle into line
writeline to handle "text"
```

### Error Handling
```
try
  $ code that might fail
handle error
  $ handle the error
end
```

## TextMate Grammar

The extension uses a custom TextMate grammar (`easylang.tmLanguage.json`) that defines tokenization rules for all EasyLang language features. This ensures consistent and accurate syntax highlighting across different color themes in VS Code.
