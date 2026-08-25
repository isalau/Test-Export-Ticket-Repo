# Test-Export-Ticket-Repo
Test Export Ticket Repo

## Project board sync

The `Sync project boards` workflow checks every five minutes for tickets that exist on both `Client Board` and `Event Bus Board`, then copies the `Status` from the first board to the second. It can also be started manually from the Actions tab.

Repository setup:

1. Create a fine-grained personal access token with `Projects: Read and write` access for the account that owns both boards.
2. Add it as the repository secret `PROJECTS_TOKEN`.
3. If either board is owned by a different account, add repository variables named `CLIENT_BOARD_OWNER` and `EVENT_BUS_BOARD_OWNER`. Otherwise, both default to the repository owner.

The status option names must exist on both boards. Because GitHub Actions does not support a Projects v2 item event trigger, synchronization is scheduled rather than immediate. Updating `Event Bus Board` does not create a loop because only `Client Board` is read as the source.
