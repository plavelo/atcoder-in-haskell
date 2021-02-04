# Exhaustive search
## [ABC087-B Coins](https://atcoder.jp/contests/abc087/tasks/abc087_b)
```haskell
import Control.Monad

main = do
  [a, b, c, x] <- replicateM 4 readLn
  print . length $ [(i, j, k) | i <- [0 .. a], j <- [0 .. b], k <- [0 .. c], i * 500 + j * 100 + k * 50 == x]
```
