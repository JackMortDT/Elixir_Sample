## Data Types
### Numbers
In Elixir we have 2 types, _Integers_ with no decimal places and _Floats_ with decimal places

```elixir
## Integers
iex> 42
42
iex> 100_000_000
100000000

## Floats
iex> 42.03
42.03
iex> 10_200.09
10200.09
```

### Atoms
```elixir
:named_constant
```
Examples
```elixir
## True and false are atoms
iex> true == :true
true
iex> false == :false
true

## Nil is an atom
nil == :nil
```

### Binaries
Examples

*01101000 01100101 01101100 01101100 01101111*

##### Is represented in elixir as this Binary:
*<<104, 101, 108, 108, 111>>*

##### Which can also be written this way:
```elixir
iex> <<104, 101, 108, 108, 111>>
"hello"
```

### Strings
Strings are just binaries
```elixir
iex> "hello" == <<104, 101, 108, 108, 111>>
true

## You can write a multiline string with """  """
iex> """ 
...> Hello Elixir
...> This is a multiline String.
...> """
"Hello Elixir\nThis is a multiline String."
```

### Maps
*%{key: value, ...}*

Examples
```elixir
iex> person = %{
...> name: "Luis Sastré",
...> age: 22,
...> developer: true
...> }
%{name: "Luis sastré", age: 22, developer: true}
iex> person.name
"Luis Sastré"
iex> person.age
22
iex> person.developer
true
```

### Tuples
Tuples are collection of values

*{value, value, value, ...}*

Examples

```elixir
iex> user = {"Luis", 23, false}
{"Luis", 23, false}
iex> elem(user, 0)
"Luis"
iex> elem(user, 1)
23
iex> elem(user, 2)
false
iex> elem(user, 3)
** (ArgumentError) argument error
    :erlang.element(4, {"Luis", 23, false})

```
##### You can update an element in an existing Tuple
```elixir
iex> put_elem(user, 0, "Sastré")
{"Sastré", 23, false}
```

### List

*[value, value, value, ...]*

* Elixir lisis are head/tail pairs
* Immutability makes them memory efficient
* Prepending is *FAST*
* Appending in *SLOW*
* Inserting elements can be slow
* Reading the whole list can be slow

#### Character Lists
[integer, integer, ...]

Examples
```elixir
## Shorthand notation
iex> 'hello'
'hello'

## Under the hood
iex> [104, 101, 108, 108, 111]
'hello'
```

### Functions

fn(args) -> ... end

Examples
```elixir
iex> add = fn(a, b) ->
...> a + b
...> end

iex> add.(10, 9)
19
```

### Other Basic Types

* PIDs
* References
* Records
* Port references

---
### How to check Types

_is_type(value)_

Example
```elixir
iex> is_atom(:elixir)
true
iex> is_list([1,2,3])
true
iex> is_map(%{language: "Elixir"})
true
iex> is_
is_atom/1         is_binary/1       is_bitstring/1    is_boolean/1
is_float/1        is_function/1     is_function/2     is_integer/1
is_list/1         is_map/1          is_nil/1          is_number/1
is_pid/1          is_port/1         is_reference/1    is_tuple/1
```