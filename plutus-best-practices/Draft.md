### Don't reinvent the wheel <sup>`Draft`</sup>

Plutus is full of useful, well-tuned functions. Before implementing a common task, make sure there isn't a function designed to do just that.

#### Examples

If you want to collect a subset of all the outputs at the script address, use `collectFromScriptFilter` instead of manually filtering the outputs obtained by `collectFromScript`:

❌

```haskell
filteredOutputs flt utxo redeemer =
    let ourUtxo :: Map.Map TxOutRef ChainIndexTxOut
        ourUtxo = Map.filterWithKey flt utxo
    in collectFromScript ourUtxo redeemer
```

✅

```haskell
filteredOutputs = collectFromScriptFilter flt utxo redeemer
```

#### Why

- Less error-prone code
- Clear and concise
- It takes advantage of optimizations made by the Plutus team.

### <sup>`Draft`</sup>

#### Examples

❌

```haskell

```

✅

```haskell

```

#### Why

### <sup>`Draft`</sup>

#### Examples

❌

```haskell

```

✅

```haskell

```

#### Why

### <sup>`Draft`</sup>

#### Examples

❌

```haskell

```

✅

```haskell

```

#### Why
