# Test-Export-Ticket-Repo
Test Export Ticket Repo

## Project board sync

The `Sync project boards` workflow copies a ticket's `Status` from `Client Board` to the matching ticket on `Event Bus Board` when the ticket exists on both boards.

Repository setup:

1. Create a fine-grained personal access token with `Projects: Read and write` access for the account that owns both boards.
2. Add it as the repository secret `PROJECTS_TOKEN`.
3. If either board is owned by a different account, add repository variables named `CLIENT_BOARD_OWNER` and `EVENT_BUS_BOARD_OWNER`. Otherwise, both default to the repository owner.

The status option names must exist on both boards. The workflow listens for edits on all Projects v2 boards but only acts on edits originating from `Client Board`, so updating `Event Bus Board` does not create a loop.
