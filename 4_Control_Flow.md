## Control Flow
### What is Control Flow
Almost every program needs behave differently depending on the situation, The features which allow it to do this are called **Control Flow** features.
#### Basic Control Flow: cond
Runs the first block where the expression is truthy
```elixir
cond do
  expr -> code
  true -> default
end
```
And there is a simple example in action
```elixir
cond do
  1 + 1 == 1 ->
    "This will never happen"
  2 * 2 != 4 ->
    "Nor this"
  true ->
    "This will"
end
```
#### Basic Control Flow: case
The case macro can be use to run an specific block of code depending of the value of an expression
```elixir
case expr do
  output -> code
  _other -> default
end
```
Here is an example
```elixir
case Stripe.Customer.create(attrs) do
  {:ok, customer} ->
    "A customer was created with ID #{customer.id}"
  {:error, reason} ->
    "Customer could not be created because #{reason}"
  other ->
    "An unknown error ocurred. #{other}"
end
```
#### Basic Control Flow: if
This expression return a true value
```elixir
if expr do
  code
end
```
Here is an example
```elixir
if 1 + 1 == 3 do
  "This won't happen"
else
  "This will happen"
end
```
And you can use **if** clause if the value exist
```elixir
if user.admin? do
  # Display the admin interface
else
  # Display the normal user interface
end
```
**Use cond for else if clauses**
```elixir
if 1 + 1 = 3
  "The universe is crumbling"
elsif 1 + 1 == 2
  "Everything is fine"
elsif 5 + 1 == 42
  "The meaning of life, the universe..."
else
  "I give up"
end
```
Or you can use this syntax
```elixir
cond do
  1 + 1 == 3  ->  "The universe is crumbling"
  1 + 1 == 2  ->  "Everything is fine"
  5 + 1 == 42 ->  "The meaning of life..."
  true -> "I give up"
end
```

#### Basic Control Flow: unless
The code in the block run unless the expression is truth
```elixir
unless expr do
  code
end
```
Example:
```elixir
unless 1 + 1 == 3 do
  "The laws of math still hold true"
end
```

### Pattern Matching
```elixir
def blank?(value) do
  # Determine whether value is nil, false, or ""
end
```
**Case statement**
```elixir
def blank?(value) do
  case value do
    nil     ->  true
    false   ->  true
    ""      ->  true
    _other  ->  false
  end
end
```
**With pattern matching**
```elixir
def blank?(nil),    do: true
def blank?(false),  do: true
def blank?(""),     do: true
def blank?(_other)  do: false
```
