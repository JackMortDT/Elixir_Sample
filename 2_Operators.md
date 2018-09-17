## Operators

### The Match Operator

```elixir
iex> name = "Luis"
"Luis"

iex> name
"Luis"
```

Variables names can be rebound

```elixir
iex> name = "Luis"
"Luis"
iex> name = "Enrique"
"Enrique"
iex> name
"Enrique"
```

Complex, multi-part patterns can be used

```elixir
iex> {name, age} = {"Luis", 22}
{"Luis", 22}
iex> name
"Luis"
iex> age
22
```

Variables only bind once per pattern

The match operator can be used to make assertions

```elixir
iex> {"Luis", age} = {"Luis", 30}
{"Luis", 30}
iex> {"Luis", age} = {"Enrique", 30}
** (MatchError) no match of right hand side value: {"Enrique", 23}
    (stdlib) erl_eval.erl:450: :erl_eval.expr/5
    (iex) lib/iex/evaluator.ex:249: IEx.Evaluator.handle_eval/5
    (iex) lib/iex/evaluator.ex:229: IEx.Evaluator.do_eval/3
    (iex) lib/iex/evaluator.ex:207: IEx.Evaluator.eval/3
    (iex) lib/iex/evaluator.ex:94: IEx.Evaluator.loop/1
    (iex) lib/iex/evaluator.ex:24: IEx.Evaluator.init/4
```

Fail quickly if assertions aren't true

##### All Elixir types can be matched

_Matching maps_
```elixir
iex> %{name: name, age: age} = %{name: "Luis", age: 24}
%{age: 24, name: "Luis"}
```
_Matching binaries_
```elixir
iex> %Person{} = %Person{name: "Luis", age: 22}

iex> "Hello, " <> word = "Hello, World!"
"Hello, World!"
```

### The Math Operators
Standar math operators are included
```elixir
iex> 1 + 1
2
iex> 1 - 1
0
iex> 20 / 2
10.0
iex> 10 * 5
50
iex> rem(15, 5)
0
iex> rem(15, 2)
1
```

### Comparison Operators
Compare equality with _==_ or _===_ and _!=_ or _!==_

```elixir
iex> "Luis" == "Luis"
true
iex> 1 == 1.0
true
iex> 1 === 1.0
false
iex> 1 != 2
true
iex> 1 != 1.0
false
iex> 1 !== 1.0
true
iex> 2 > 1
true
iex> 1 >= 1
true
iex> 1 < 2
true
iex> 1 <= 2
true
```

### List Operators
Assert an element is present in a list
```elixir
iex> "Luis" in ["Luis", "Enrique", "Sastré"]
true
iex> "Luiss" in ["Luis", "Enrique", "Sastré"]
false
```

you can combine two list with **++** 
```elixir
iex> [1, 2, 3] ++ [4]
[1, 2, 3, 4]
```
And with **--** you can remove elements from a list
```elixir
iex> [1,2,3] -- [2, 3]
[1]
```
**|** operator is used to prepend to a list
```elixir
iex> list = [1, 2, 3]
[1, 2, 3]
iex> [5 | list]
[5, 1, 2, 3]
```
You can combine **|** with **=** for complex matcher
```elixir
iex> [head | tail] = [1, 2, 3]
[1, 2, 3]
iex> head
1
iex> tail
[2, 3]
iex> [a, b, c | tail] = [1, 2, 3, 4]
[1, 2, 3, 4]
iex> a
1
iex> b
2
iex> c
3
iex> tail
[4]
```

### Binary Operators
We can concatenate 2 binaries with **<>**
```elixir
iex> "Hello" <> " Elixir"
"Hello Elixir"
```

Or interpolate values into binaries with **#{}**
```elixir
iex> "50 * 50 = #{50 * 50}"
"50 * 50 = 2500"
iex> name = "Elixir"
"Elixir
iex> "Hello #{name}"
"Hello Elixir"
```

### Logical Operators
Assert tow expressions are thuthy with **&&**
```elixir
iex> 1 == 1.0 && 1 === 1.0 
false
iex> 1 == 1.0 && 1.0 === 1.0
true
```
Assert one of two expressions with or **||**
```elixir
iex> 1 == 2 || 1 == 1
true
iex> "Luis" == "Luus" || 1 === 1.0
false
iex> 1 || nil
1
```







