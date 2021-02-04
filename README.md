# atcoder-in-haskell
Competitive programming using Haskell :tada:

## I/O
### Input
* Reads a string from stdin and outputs it.
```haskell
main = do
  result <- getLine
  print result

# input
hello

# output
"hello"
```

* Converts a single numeric string to a number.
```haskell
main = do
  result <- readLn :: IO Int
  print result

# input
1

# output
1
```

* Convert a space-delimited numeric string to numbers.
```haskell
main = do
  result <- map read . words <$> getLine :: IO [Int]
  print result

# input
1 2 3

# output
[1,2,3]
```

* It can also be written as follows.
```haskell
main = do
  [a, b, c] <- map read . words <$> getLine :: IO [Int]
  print (a + b + c)

# ipunt
1 2 3

# output
6
```

* Convert N lines of space-delimited numeric string to numbers.

```haskell
import Control.Monad

main = do
  let n = 2
  result <- replicateM n $ map read . words <$> getLine :: IO [[Int]]
  print result

# input
1 2 3
4 5 6

# output
[[1,2,3],[4,5,6]]
```

* The String type is internally represented as a linked list of characters, which is disadvantageous in terms of processing speed. In such a case, ByteString can be used to speed up the input.

```haskell
import qualified Data.ByteString.Char8 as BC
import Data.Maybe

main = do
  result <- map (fst . fromJust . BC.readInt) . BC.words <$> BC.getLine :: IO [Int]
  print result

# input
1 2 3

# output
[1,2,3]
```

```haskell
import qualified Data.ByteString.Char8 as BC
import Data.Maybe

main = do
  result <- map (fst . fromJust . BC.readInt) . BC.lines <$> BC.getContents :: IO [Int]
  print result

# input
1
2
3

# output
[1,2,3]
```

```haskell
import qualified Data.ByteString.Char8 as BC
import Data.Maybe

main = do
  result <- map (map (fst . fromJust . BC.readInt) . BC.words) . BC.lines <$> BC.getContents :: IO [[Int]]
  print result

# input
1 2 3
4 5 6

# output
[[1,2,3],[4,5,6]]
```

## Output
* If you want to output a String, you can use putStrLn or putStr.
```haskell
main = do
  [a, b, c] <- map read . words <$> getLine :: IO [Int]
  putStrLn . unwords $ map show [a, b, c]
```
