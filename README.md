# UiPath Battleship via Email

This project is a Battleship game automation built in UiPath.
Players interact with the game entirely through email messages.

All messages must be sent to the configured robot email address.

> [!WARNING]
>
> * Excessive spam or repeated requests may cause unexpected game behavior.
>
> * Using a non-existent email address is guaranteed to break the robot workflow.
>
> * Commands must be sent as new standalone emails. Replying to robot messages is not supported.

---

# How to Set Up

1. Connect your Outlook email to Orchestrator.
2. Pull the repository.
3. Run UiPath Studio to compile the project. **Update** *Functions\Email\Send.xaml* with your Outlook account.
4. Publish the project to your Orchestrator.
5. Set up the Machine template.
6. Set up the Event Trigger. Make sure you are watching the required folder. The process does not know what to do with emails unrelated to the game.
7. Run the Job on your local machine using UiPath Assistant.
8. Enjoy!

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
* Invalid commands or incorrect ship placements will be rejected.
* The game starts only after both players have successfully placed all their ships.

---

# Technologies Used

* UiPath (Outlook Activities)
* Orchestrator Event Triggers
* DataTables
* File-based session management
* Excel (Local storage)
* HTML email templates
* RegEx
