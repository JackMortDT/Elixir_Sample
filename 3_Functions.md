## Functions, Modules and Structs

### Anonymous Functions
Is simple to define an anonymous function in Elixir
```elixir
iex> add = fn(num_1, num_2) ->
...>   num_1 + num_2
...> end

iex> add.(10, 9)
19
iex> add.(1, 1.9)
2.9

iex> sum = add
iex> add.(1,2)
3
iex> sum(1, 2)
3
```

### Named Functions
The way to define named functions is
```elixir
def add(a, b) do
  a + b
end
```

But named functions can only be defined in modules
```elixir
iex> defmodule Calculator do
...>  def add(a, b) do
...>     a + b
...>   end
...> end

iex> Calculator.add(1, 2)
3
```

#### Modules: Nesting
Modules can be nested
```elixir
defmodule Math do
  defmodule Division do
    def divide(a, b) do
     a / b
    end
  end
end

Math.Division.divide(15, 5)
3
```

### Private Functions

Can be define with de defp macro
```elixir
defmodule Math do
  def add(a, b) do
    a + b
  end

  defp sub(a, b) do
    a - b
  end
end

Math.add(1, 2)
3
Math.sub(2, 1)
** (UndefinedFunctionError) function Math.sub/2 is undefined or private
    Math.sub(2, 1)
```

#### Using other Modules: Aliasing

```elixir
defmodule MyModule do
  def my_function(args) do
    Really.Long.OtherModule.other_function
  end
end
```
You can put alias for other modules name
```elixir
defmodule MyModule do
  alias Really.Long.OtherModule, as: O

  def my_function(args) do
    O.other_function
  end
end
```
Or you can import other modules
```elixir
defmodule MyModule do
  import Really.Long.OtherModule

  def my_function(args) do
    other_function
  end
end
```
And when you import you can import only one function if it is necessary
```elixir
import Really.Long.OtherModule,
       only: [other_function: 1]
```
And you can import all functions except one with the word except
```elixir
import Really.Long.OtherModule,
       except: [other_function: 1]
```
Using functions from other modules
```elixir
defmodule MyModule do
  defdelegate function(args1, args2), to: Really.Long.OtherModule,
                                      as: my_function
end

MyModuel.my_function(1, 2) ## Calls OtherModule.function(1, 2)
```

##### Documentation
You can documentate your modules or your functions

* @moduledoc: Documentation for your module
```elixir
defmodule Math do
  @moduledoc """
    Defines some basic math operations functions.
  """
end
```
* @doc: Documentation for your function
```elixir
@doc """
  Adds tow integers together

  Example:
  add(1, 2)
  3
"""

def add(a, b) do
  a + b
end
```

### Structs

defstruct attr1: val, attr2: ...

```elixir
defmodule User do
  defstruct name: nil,
            age: nil
end

%User{}
%User{age: nil, name: nil}

%User{name: "Luis", age: 22}
%User{age: 22, name: "Luis"}
```

 







