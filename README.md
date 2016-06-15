# conduit-merge

Merge multiple conduits into one.

```haskell
module Data.Conduit.Merge where

mergeSources :: (Ord a, Monad m) => [Source m a] -> Producer m a
```

## Example

```haskell
main = do
    inputFileNames <- getArgs
    let inputs = [sourceFile file =$= Conduit.lines | file <- inputFileNames]
    runResourceT $ mergeSources inputs $$ sinkStdoutLn
```