## Playlist

Use slices to plan which songs from a playlist you have time for.

Your program should:
* Print the first and last songs in the playlist.
* Ask how many songs the user has time for, and print a list of that many songs from the start of the playlist.
* Remove those songs from the playlist, and print the songs that are left.

Here is example output from running this program:

```
First song: Morning Coffee
Last song: Goodnight
How many songs do you have time for? 2
You will hear: ['Morning Coffee', 'Bus Window']
Saved for later: ['Rainy Day', 'Dance Break', 'Road Trip', 'Goodnight']
```

`playlist[-1]` is the last song, however long the playlist is. `playlist[:n]` makes a new list of the first n songs and leaves playlist alone. To actually remove them, store the rest of the list back in `playlist: playlist = playlist[n:]` keeps everything from index n to the end.

### Answer

```python
def main():
    playlist = ["Morning Coffee", "Bus Window", "Rainy Day", "Dance Break", "Road Trip", "Goodnight"]
    print(f"First song: {playlist[0]}")
    print(f"Last song: {playlist[-1]}")
    n = int(input("How many songs do you have time for? "))
    print(f"You will hear: {playlist[:n]}")
    playlist = playlist[n:]
    print(f"Saved for later: {playlist}")


if __name__ == "__main__":
    main()
```