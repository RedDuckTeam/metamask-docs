---
title: 'Sign Messages on Solana - MetaMask Connect'
sidebar_label: Sign messages
description: Request offchain cryptographic signatures from users on Solana using MetaMask Connect's signMessage Wallet Standard feature.
keywords:
  [
    solana sign message,
    signMessage,
    wallet-standard,
    offchain signature,
    message verification,
    metamask,
    solana,
  ]
---

# Sign messages

Your dapp can ask users to sign a message with their Solana account; for example, to verify ownership or authorize an action.

## Prerequisites

Follow the [quickstart](../../quickstart/javascript.md) to install, initialize, and connect the Solana client.

## Use `solana:signMessage`

Use the [`solana:signMessage`](../../reference/methods.md#supported-wallet-standard-features) feature to request a human-readable signature that doesn't need to be verified onchain.

The following example requests a signed message using MetaMask:

```javascript
import { createSolanaClient } from '@metamask/connect-solana'

const solanaClient = await createSolanaClient({
  dapp: {
    name: 'My Solana Dapp',
    url: window.location.origin,
  },
})

const wallet = solanaClient.getWallet()

// Connect and get the user's account
const { accounts } = await wallet.features['standard:connect'].connect()

async function signMessage() {
  const message = new TextEncoder().encode('Only good humans allowed. Paw-thorize yourself.')

  const [{ signature }] = await wallet.features['solana:signMessage'].signMessage({
    account: accounts[0],
    message,
  })

  return signature
}
```

## Verify a signature offchain

<iframe className="mt-6" width="100%" height="480px" frameBorder="0" title="Sign and verify a Solana message" src="https://plgrnd.io/embed?theme=auto&ref=metamask-docs#flow=N4IgbiBcDMA0IDsD2ATApgZygbVASxShAGMBGEeAFwE8AHNIgYQHkBZVgUQDkAVCkWkgx5KeJAiigAHlAAM8alAC0pACyyAvvBQBDSjskhKaKZSIBlPAHMEsAASUAFmgR2waAE54AZtTtJvb2JHHTwEAB0EcwBJAHEuSDsOFAAmAFY00gBOf3cPB2c7AFUeADElAA47ACNqYwx-bwK0OwBbTAwdKzR7DEckAHdXap0MNDSKpRdiVDQUOwAKJxaBnQAbNbRKOw8tgFcPBAaPHQGauswASgA6OwA1DgAlaNKATTsENDmG8TW-ZbstD21TWeGIdgA1mhqNcQBotPhCJAQBDyFQ6AxkQBpDivAAKAEFoo9+IJhKJxIYZJB5CBFDStCBdPpJPDYIiiChZPwaPQiAARaLmPEAGQJr1JQhEYgkkGkUGg6gUygAbIzmQY5UYTGZkXCESACERKGijBiiDwOAANPjwMnSyla6m0+kVTTaPSa0DGUxEZgIP52KxIVB2Rx7Vo6I52dZrQZzW5405KJxILwALxa1CQBzGa28sLZHORGFNvMxIBi8Ul5JlVIVSrpUAA7O6mZ7WQajciUGXzcjBcKxRK7VKKbL5ZA0ikXVAVap1R2tT7dSB9ezDUjwH2+ciHs83gB9KtcAk8IqPDg1h0TkDUxWzyCkNJtjWdjfdowpHn9kCWm3XuO9Y0sqkApNAr5Lt6Op+gGfjBqG4aRtGsbxigibJqmGZZjmHh5t4ACE67FuA37oruID7i8rzHnEp7npegF1k6DaPuBkEsnKRabkQxDeD+FEsOw3C2gIY7MZO0AQaB0AzounHQb6yI8IUYwzAg8xUW8djBGgxAQg0AKdO0djCDYegHC0XShEc2zhCABH2XYYQYMYOjzAEdj2dcTlRvM3ihGsGC3LELieHoLSRlCDQ6B8aBnE4HiDKcOh+FCdChB4hYaAAuvAczdFgkC4DxyJSNQUwoN0h6HqiShAiCYJYtCSheFYjiUEoXJKGEQKdZs3hmPAGC4cQFaovwI0HGNAASfmbEQdUNaCxDNRVbUdTyOgeN0q5cltO1bHNGkLT2sg9QgfVKANZhdlu5WVdVtWkPVXhgBFa2tdYHVKKWr14O9xifTdk2jeNppTR4s3zeD-2A2gn0bUNRjbbtRClgdu3HSgp0gH9tBvR9LUg3dRAPQVaA1SaKY6l97WdX97QYJ03TXWgg2g9NFYmpzUNoNjuPUyudObVQqNbOjZbi5QAsVozHRdGgbMc6TZUVRTNV-WZCAWbsIudb2F1XSDw1g5LvPQydcsvdrutK0jmMSz2UuHTLMOci9vV7P17O3R+93q1VlOHkLtNI0oYAvUzLNKybeNm8iPOm1zsvGi9wsO2LrtEJHjtu1bOdRwrrMk-7ZOB09WvWDrlCWfrEc29XdvK8jkNjebyd86nJaN+Ztd65nKPZ8iudZ1j7sj73Nd16XJHk0HNVLcCK2I99nWR-Vy9NcTvsW+De-dyiL3Ldv61r3nhd54fG8n6tO8q2XauPcHlApDTpj12Ab-R4rLd78aZF44pwnl+d+nVB76GHqRK+ICv5KB-iXXeqs7wV2DlXPuddw5wNtv3WOu9O7tx7gfEB6Dp4D3PmPJ20DKH5xxhWbBTdcF-2QfPJ6S9Gp3zPvTCOb9b7A3wUAvmi0IZg0PuwleLUIHSxzoAyB48C4j14VvThzCcoaCAA" sandbox="allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox" allow="clipboard-write" loading="lazy"></iframe>

## Next steps

- [Sign in with Solana (SIWS)](siws.md) to authenticate users with domain-bound, phishing-resistant sign-in messages.
- [Send a legacy transaction](../send-transactions/legacy.md) to transfer SOL or interact with Solana programs.
- [Send a versioned transaction](../send-transactions/versioned.md) to use Address Lookup Tables for complex operations.
- [MetaMask Connect Solana methods](../../reference/methods.md) for the full list of Wallet Standard features.
