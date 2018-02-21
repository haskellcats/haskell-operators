# Operator Usage Examples

## && ||
```
> True && False
False

> True || False
True
```

## == /=

```
> 'a' == 'b'
False

> 'a' /= 'b'
True
```

## < <= > >=

```
> 99 <= 99
True

> 99 < 99
False
```

## unary -

```
> let x = 99 in -x
-99
```

## /

```
> sqrt 2 / 2
0.7071067811865476
```

## **

The usual pow operation for fractional numbers. Both 2's below are Doubles.

```
> sqrt 2 ** 2
2.0000000000000004
```

## ^

Power for integral numbers. In this example both 2 and 64 are Integers.

```
> 2^64
18446744073709551616
```

## ^^

Here 12 is an Integer. ^^ raises a fractional number to an integer power
by the equivalent of repeated multiplication.

```
> 1.0594630943592953 ^^ 12
2.0
```

## <$>

```
> chr <$> Just 65
Just 'A'

> fmap chr (Just 65) -- same thing
Just 'A'

```

Note: `chr` is not in the default Prelude. It's available in the Data.Char
module.

## <$

```
> 'z' <$ [1,2,3,4]
"zzzz"

> fmap (const 'z') [1,2,3,4] -- same thing
"zzzz"
```

## <*>

The combination of `<$>` followed by a chain of `<*>` is an old idiom
of functional programming, formalized in Haskell as part of the
type class Applicative.

```
> (,) <$> Just 'A' <*> Just 99 -- the idiom
Just ('A',99)

> liftA2 (,) (Just 'A') (Just 99) -- same thing
Just ('A',99)

> Just chr <*> Just 3
Just 'A'

> Just (<) <*> Just 'a' <*> Just 'z'
Just True

> Just (<) <*> Nothing <*> Just 'z'
Nothing
```

## <*

```
```

## *>

```
```

## >>=

```
> getLine >>= \line -> sendEmail "nowhere@example.com" line
<IO ()>

> do {line <- getLine; sendEmail "nowhere@example.com" line} -- same thing
<IO ()>

> getLine >>= sendEmail "nowhere@example.com" -- same thing
<IO ()>
```

## >>

```
> ringBell >> sleep 3 >> ringBell >> sleep 2
<IO ()>

> do {ringBell; sleep 3; ringBell; sleep 2} -- same thing
<IO ()>

> Just 'A' >> Just 99 >> Just "foo" >> Just [1,2,3]
Just [1,2,3]

> Just 'A' >> Nothing >> Just "foo" >> Just [1,2,3]
Nothing
```

## =<<

```
> deleteFile =<< readFile =<< getLine
<IO ()>
```

## .

```
> (chr . (+1) . ord) 'A'
'B'

> let f = chr . (+1) . ord in f 'A' -- same thing
'B'
```

## $

Low precedence function application operator. I recommend not using this to
be lazy with parentheses, but rather to begin multiline "block" arguments
to higher order functions as shown below.

```
> sum (map ord "Hello World")
1052

> sum $ map ord "Hello World" -- same thing
1052
```

```
forM_ [0..n-1] $ \i -> do
  print i
  sleep 1

forM_ [0..n-1] (\i -> do
  print i
  sleep 1 ) -- same thing
```

## $!

`$!` is $ which effectively evaluates the argument before applying a function.
It is equivalent to using seq or bang patterns as shown below. Usually when
you need to control evaluation you want to use bang patterns, strict record
fields, or seq instead.

```
> const 'A' undefined
'A'

> const 'A' $! undefined
*** Exception: undefined

> let !x = undefined in const 'A' x -- same thing
*** Exception: undefined

> let x = undefined in x `seq` const 'A' x -- same thing
*** Exception: undefined

> const 'A' $! [1,2,undefined,4]
'A'
```

## ++

```
> "Hello" ++ " " ++ "World"
"Hello World"

> [1,2] ++ [3,4]
[1,2,3,4]
```

## !!

```
> "Hello" !! 4
'o'

> "Hello" !! 5
*** Exception: !!: index too large
```
