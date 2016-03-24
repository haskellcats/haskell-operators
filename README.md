= "All Haskell Operators"

|Operator     |Type                                          |Notes|
|:-----------:|----------------------------------------------|-----|
| @&& ||@     | @Bool -> Bool -> Bool@                       ||
| @== /= @    | @Eq a => a -> a -> Bool@                     ||
| @< > <= >=@ | @Ord a => a -> a -> Bool@                    ||
| @+, -, * @  | @Num a => a -> a -> a@                       ||
| unary -     | @Num a => a -> a@                            ||
| @/@         | @Fractional a => a -> a -> a@                ||
| @ ** @      | @Floating a => a -> a -> a@                  ||
| @^ @        | @(Num a, Integral b) => a -> b -> a@         ||
| @^^@        | @(Fractional a, Integral b) => a -> b -> a@  ||
| @<$>@       | @Functor f => (a -> b) -> f a -> f b@        ||
| @ <$ @      | @Functor f => a -> f b -> f a@               ||
| @ <*>@      | @Applicative f => f (a -> b) -> f a -> f b@  ||
| @ <* @      | @Applicative f => f a -> f b -> f a@         ||
| @ *> @      | @Applicative f => f a -> f b -> f b@         ||
| @ >>= @     | @Monad m => m a -> (a -> m b) -> m b@        ||
| @>>@        | @Monad m => m a -> m b -> m b@               ||
| @=<<@       | @Monad m => (a -> m b) -> m a -> m b@        ||
| @.@         | @(b -> c) -> (a -> b) -> a -> c@             ||
| @$, $!@     | @(a -> b) -> a -> b@                         ||
| @++@        | @[a] -> [a] -> [a]@                          ||
| @!!@        | @[a] -> Int -> a@                            ||
