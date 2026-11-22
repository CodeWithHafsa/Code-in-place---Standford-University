## Team Roster
Sign new players up for a team.

Your program should:
* Store the teams as a dictionary. Each key is a team name, and each value is a list of the players on that team.
* Keep asking for a new player's name until the user presses enter instead of typing a name. For each player, ask which team they want and add them to that team's list. If there is no such team, print a message instead.
* At the end, print each team, how many players it has, and who they are.

Here is example output from running this program:

```
New player's name: Dev
Which team, red or blue? blue
New player's name: Eli
Which team, red or blue? green
There is no green team.
New player's name: Fay
Which team, red or blue? red
New player's name:
red team has 3 players: ['Ana', 'Ben', 'Fay']
blue team has 2 players: ['Cleo', 'Dev']
```

`teams[team]` is a list, so the program can append to it just like any other list. The dictionary itself does not have `append`. Looping over a dictionary gives you each key, so for `team` in `teams` goes through the team names.


### Answer:

```python
def main():
    teams = {
        "red": ["Ana", "Ben"],
        "blue": ["Cleo"],
    }
    name = input("New player's name: ")
    while name != "":
        team = input("Which team, red or blue? ")
        if team in teams:
            teams[team].append(name)
        else:
            print(f"There is no {team} team.")
        name = input("New player's name: ")
    for team in teams:
        players = teams[team]
        print(f"{team} team has {len(players)} players: {players}")


if __name__ == "__main__":
    main()
```