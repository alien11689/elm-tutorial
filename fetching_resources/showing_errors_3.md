# Showing Errors 3

In the previous section we required a `showErrorAddress` in Players.Update.

We need to provide this address and do map it to the main action we want (`ShowError`).

## Auxiliary mailbox

Unfortunately StartApp doesn't give a mechanism to send messages to its address from `update`. We need to provide our own mailbox for this.

Create __src/Mailboxes.elm__:

```elm
module Mailboxes (..) where

import Actions exposing (..)

actionsMailbox : Signal.Mailbox Action
actionsMailbox =
  Signal.mailbox NoOp
```

Here we have a mailbox where we can send any root action we want to run.