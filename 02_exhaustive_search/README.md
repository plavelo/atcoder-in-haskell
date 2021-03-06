# Exhaustive search
## [ABC087-B Coins](https://atcoder.jp/contests/abc087/tasks/abc087_b)
* Find the number of combinations of ways to make the total amount of A 500 yen coins, B 100 yen coins, and C 50 yen coins equal X yen.
```haskell
import Control.Monad

main = do
  [a, b, c, x] <- replicateM 4 readLn
  print . length $ [(i, j, k) | i <- [0 .. a], j <- [0 .. b], k <- [0 .. c], i * 500 + j * 100 + k * 50 == x]
```

## [ARC004-A The longest distance](https://atcoder.jp/contests/arc004/tasks/arc004_1)
* Find the longest line segment formed by connecting two of the N points in the plane.
```haskell
import Control.Monad

main = do
  n <- readLn
  p <- replicateM n $ map read . words <$> getLine
  print $ maximum [sqrt . fromIntegral $ (head j - head i) ^ 2 + (last j - last i) ^ 2 | i <- p, j <- p]
```