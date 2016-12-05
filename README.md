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
