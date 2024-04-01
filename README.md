# nostr-P2PK
Cashu (NUT-11) P2PK Cashu-based micropayments client-relay note posting and relay-relay note reconciliation

## This landing page will be use to stage updates to NDK and strfry to implement ecash incentivized note posting and inter-relay reconciliation through negentropy.
#### GLOSSARY:
* `ecash-taco` - A JSON containing
    ```
    {
    "note": {...a  signed kind-01 note in JSON format}
    "relay-mint": "address of an ecash mint"
    "relay-pubkey": "the npub the P2PK ecash is locked to"
    "ecash": "...Ecash string locked to npub..."
    "relay-fee": 1000
    }
    ```
* `relay-mint` - address of the Cashu mint that relay requires payment at
* `user-mint` - address of the Cashu mint that user holds its Ecash balance
* `relay-pubkey` - designated npub of the relay to which P2PK Ecash will be locked for payments
* `user-pubkey` - designated npub of the user to which P2PK Ecash will be locked for returned payments
* `relay-fee` - mSAT value of relay fee

### STAGE 1: Basic implementation client-to-relay submission for testing
#### PROGRESS: Update NDK to send kind-01 notes wrapped in `ecash-taco`
* (TODO) Update NDK to request a designated `relay-mint` and `relay-fee` from a relay
* (TODO) Update NDK to access a Cashu mint to check user Ecash balance
* (TODO) Update NDK to transfer a Cashu mint balance to a designated `relay-mint`
* (TODO) Update NDK to request `relay-mint` to lock Ecash to `relay-pubkey` in denomination `relay-fee`
* (TODO) Update NDK to wrap kind-01 notes in an `ecash-taco`
* (TODO) Update NDK to submit kind-01 note to relay in an `ecash-taco`

### PROGRESS: Update strfy to handle kind-01 notes wrapped in `ecash-taco`
* (TODO) Update strfry to serve a designated `relay-mint` and `relay-fee` to requesting clients
* (TODO) Update strfry to recognize `ecash-taco` wrapped kind-01 notes
* (TODO) Update strfry to request unlock of `ecash-taco` Ecash from designated `relay-mint`
* (TODO) Update strfry to interface with a designated ecash mint

### STAGE 2: Basic implementation of relay-to-relay incentivized negentropy reconciliation
* (PLAN) Choose communication framework
* (PLAN) Choose incentive format: pay-per-request, pay-per-data, or both
* (PLAN) Implement relay-to-relay negotiation

#### STAGE 3: Improvments to create an optimized network
* (DISCUSS) User overpay for dynamic fees; a mechanism for return payment locked to `user-pubkey` at `relay-mint` in a dynamic fee environment.
* (DISCUSS) Update NDK to subscribe to a relay's notes for currently designated `relay-fee` and `relay-mint`
* (DISCUSS) Update NDK to choose relay or relays to post to based on current `relay-fee` and `relay-mint` data for a pool of relays
* (DISCUSS) Oversight of selfish relays: NDK to check and publish user ROI from utilized relays
