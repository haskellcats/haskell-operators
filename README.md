# "All Haskell Operators"

Of course, you are free to define new operators using any symbol characters.
This table contains all the operators defined in the Prelude at the time of
this writing. There are a few operators not listed which are commonly imported
(such as `<>` from `Data.Monoid`) and some libraries define a large number of
their own (lens). This table exists to introduce "Haskell syntax" with a
gratuitous listing of operators similar to every other language manual.

|Operator     |Type                                          |Notes|
|:-----------:|----------------------------------------------|-----|
| `&& &#124;&#124;` | `Bool -> Bool -> Bool`                 |     |
| `== /= `    | `Eq a => a -> a -> Bool`                     | Value equality. |
| `< > <= >=` | `Ord a => a -> a -> Bool`                    ||
| `+ - * `    | `Num a => a -> a -> a`                       ||
| unary -     | `Num a => a -> a`                            | Special case unary operator for `negate`.<br>Doesn't work in a section,<br>use (subtract x) instead of (- x). |
| `/`         | `Fractional a => a -> a -> a`                | Use `div` `mod` or `divMod` for integer division.<br>See also `quot` `rem` and `quotRem`. |
| ` ** `      | `Floating a => a -> a -> a`                  ||
| `^ `        | `(Num a, Integral b) => a -> b -> a`         ||
| `^^`        | `(Fractional a, Integral b) => a -> b -> a`  ||
| `<$>`       | `Functor f => (a -> b) -> f a -> f b`        | Operator for fmap: `f <$> x = fmap f x` |
| ` <$ `      | `Functor f => a -> f b -> f a`               | Shorthand to do a simple replacement with fmap |
| ` <*>`      | `Applicative f => f (a -> b) -> f a -> f b`  | "Applicative function application" |
| ` <* `      | `Applicative f => f a -> f b -> f a`         | See `<$` and `>>` |
| ` *> `      | `Applicative f => f a -> f b -> f b`         | See `<$` and `>>` |
| ` >>= `     | `Monad m => m a -> (a -> m b) -> m b`        | "Monad bind" |
| `>>`        | `Monad m => m a -> m b -> m b`               | Shorthand to discard result of first action |
| `=<<`       | `Monad m => (a -> m b) -> m a -> m b`        | "Monad function application"<br>`(=<<) = flip (>>=)` |
| `.`         | `(b -> c) -> (a -> b) -> a -> c`             | Function composition |
| `$ $!`      | `(a -> b) -> a -> b`                         | Function application operator.<br>`$!` will evaluate the argument first (to WHNF). |
| `++`        | `[a] -> [a] -> [a]`                          | List concatenation. |
| `!!`        | `[a] -> Int -> a`                            | O(n) linked list indexing.<br>There's probably a better way. |
