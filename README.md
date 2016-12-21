# n00b-elixir
n00b series of learning elixir from bottom

## Day 1

```exs
# [Short] Range.new(1,n) ==> 1..n
# [Short] if <condition>, do: <sth>, else <sth> end
# [Func] String.replace(<string>, <string|char>, <string|char>)
# [Func] String.graphemes
"test" |> String.graphemes # ["t","e","s","t"]
# [Func] Enum.join
["1","2"] |> Enum.join # "12"
Enum.join(["1","2"], "-") # "1-2"
```

## Day 2

```exs
# [Func] Stream.flat_map(enumerable, fun) returns a new enumerable
# Anonymous function using & (like \ in haskell, e.g. \n -> n * 2)
Enum.map [1, 2, 3, 4], &(&1 * 2) # returns [2, 4, 6, 8], same as
Enum.map [1, 2, 3, 4], fn n -> n * 2 end # same output [2, 4, 6, 8]
```

## Day 3

```exs
# Start playing around exercism
# EEx we can embed and evaluate Elixir inside strings.
EEx.eval_string "Hello, <%= name %>!", [name: "World"]
# ? followed by a character gives you that character's Unicode code point value.
?A # return 65
# List with only valid codepoints will also be printed as string !!!
[?A] # return A
# In practice, char lists are used mostly when interfacing with Erlang
'test' |> String.graphemes # not allow
'test' |> to_string |> String.graphemes # ["t", "e", "s", "t"]
```

## Day 4

```exs
# Define a map
map = %{?A => 0}
# Access it
map[?A] # 0
map[65] # 0
# Rewrite it using put_in/2
put_in(map[?A], map[?A] + 1) # %{?A => 1}
Map.put(map, ?A, map[?A] + 1) # another helper method
# Variables in elixir is immutable, so cannot directly change list/map inside a collection iteration like Enum.each Enum.map
put_in(map[?A], map[?A] + 1) # %{?A => 1} but map itself won't change
# Enum.reduce/3
Enum.reduce(in, source, fn x, acc -> dosth(x, acc) end) # x is the current item iterated, and acc is the accumulated acc
[] |> Enum.reduce(source, fn x, acc -> dosth(x, acc) end) # using alongside with pipeline operator
# if in is char list, say 'ABC', x will be 65, 66, 67 
# Default value in function
def sum_by(x, n \\ 4) do # n is default to 4 if not specified
  x + n
end 
# Single quote in elixir is called char list while double quote is string
```

## Day 5

```exs
# Destructing (terms in js) and pattern matching
{a, b} = {1, 3} # Hash dictionary matching
# defp can be used without end
```

## Day 6

```exs
# Integer split into list
Integer.digits
# Some useful function
String.capitalize # capitalize first letter in string
Enum.join # like js .join
Enum.with_index # assign index to the list
Enum.map_join # composed with map and join for enumerable
Enum.all? # return true if given fn returns true in all items in that enum 
# Pattern matching (function overloading)
## e.g. whatever sth takes, always return true when first arg is empty string
def test("", sth) do true end 
def test(f, sth) do foo() end
## then there is stderr in first overload function, sth is unused, better to use an underscore
def test("", _)
```

## Day 7
```exs
# List length
length([1,2,3,4,5]) #5
```

## Day 8
```exs
# No need to add comma after when in function guard
def test(x) when x > 5 do something(x) end
# bitwise xor, from Bitwise module
1 ^^^ 0 #1
0 ^^^ 1 #1
0 ^^^ 0 #0
1 ^^^ 1 #0
# Kernel &&/2 returns second expression only when first expression returns true, not only for boolean
# Notice that, unlike Erlang’s and operator, this operator accepts any expression as an argument, not only booleans, however it is not allowed in guards.
```

## Day 9
```exs
# pin operator is used to match current value instead of rebinding to new one, could be useful to generalize things in guard of function clause
# https://elixirschool.com/lessons/basics/pattern-matching/
x = 1 #1
^x = 2 #error
{x, ^x} = {2, 1} #{2, 1}
x #2
```
