# Plutus and Smart Contract Best Practices (This is a WIP!)

Guidelines to help you write secure, performant, and overall better Plutus smart contracts.
(For [Marlowe](https://marlowe.iohk.io/)'s best practices, you can go [here](https://github.com/input-output-hk/marlowe-cardano/blob/main/marlowe/best-practices.md).)

## Objectives

- Reduce fees by reducing script size, computational steps, and memory units.
- Prevent errors and vulnerabilities as much as possible.
- Generate code that is easy to understand, modify, and compose.

## Structure of a guideline

Each guideline describes:

- The guideline itself (ie, prefer `X` instead of `Y`)
- Code examples with dos and don'ts
- Why we recommend this
- Status: `Draft` -> `ToReview` -> `Approved` -> `Deprecated`. Only Subject Matter Experts (SME) can approve a guideline.
- Notes (if any)

> Note:
>
> - Should we add categories?
>   - Performance: ⚡️
>   - security: 🔒
>   - style: 💅

## Example guideline

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

## Guidelines

- [Approved](Approved.md) (empty)
- [ToReview](ToReview.md) (empty)
- [Draft](Draft.md)
- [Dreprecated](Deprecated.md) (empty)
