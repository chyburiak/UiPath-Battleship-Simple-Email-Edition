# UiPath Battleship via Email

This project is a Battleship game automation built in UiPath.
Players interact with the game entirely through email messages.

All messages must be sent to:

`chyburyaks.uipath.battleship@gmail.com`

> [!WARNING]
>
> * The robot processes emails with a delay. Incoming emails are collected and processed sequentially.Excessive spam or repeated requests may cause unexpected game behaviour.
>
> * Using a non-existing email address is guaranteed to break the robot workflow.
>
> * Commands must be sent as new standalone emails. Replying to robot messages is not supported.

---

# Game Rules

Each player must place the following ships on the board:

| Ship       | Size     |
| ---------- | -------- |
| Carrier    | 5 spaces |
| Battleship | 4 spaces |
| Cruiser    | 3 spaces |
| Submarine  | 3 spaces |
| Destroyer  | 2 spaces |

---

# Email Commands

## Invite Player

Send an invitation to another player.

### Subject

```text
Invite
```

### Body

```text
{email to invite}
```

### Example

```text
example@gmail.com
```

---

## Accept Invitation

Accept a game invitation.

### Subject

```text
Accept
```

### Body

```text
{email to accept invite from}
```

### Example

```text
player@gmail.com
```

---

## Reject Invitation

Reject a game invitation.

### Subject

```text
Reject
```

### Body

```text
{email to reject invite from}
```

### Example

```text
player@gmail.com
```

---

## Place Ships

Place all ships on the game board.

### Subject

```text
Ships
```

### Body Format

```text
Carrier: {start}-{end}, Battleship: {start}-{end}, Cruiser: {start}-{end}, Submarine: {start}-{end}, Destroyer: {start}-{end}
```

### Example

```text
Carrier: E10-J10, Battleship: G1-J1, Cruiser: F3-H3, Submarine: D1-D3, Destroyer: F6-F7
```

---

## Shoot

Attack a coordinate on the enemy board.

### Subject

```text
Shoot
```

### Body

```text
{coordinates}
```

### Example

```text
A4
```

---

## Surrender

End the game and surrender.

### Subject

```text
Surrender
```

### Body

Leave empty.

---

# Notes

* Coordinates must follow the standard Battleship format.
* All commands are case-sensitive.
* Invalid commands or incorrect ship placements may be rejected.
* The game starts only after both players place all ships successfully.

---

# Technologies Used

* UiPath
* Gmail IMAP/SMTP
* DataTables
* File-based session management
* Excel as local storage
* HTML email templates
* ReGeX
