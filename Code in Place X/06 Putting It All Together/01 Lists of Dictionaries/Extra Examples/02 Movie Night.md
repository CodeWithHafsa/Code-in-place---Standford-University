## Movie Night

Help your friends pick a movie for movie night.

Your program should:
* Start with an empty list of movies.
* Keep asking for a movie and how many votes it got until the user presses enter instead of typing a movie. Store each movie as a dictionary with a title and votes.
* Print how many movies there were and which one got the most votes. If there were no movies, print a message instead.

Here is example output from running this program:

```
Movie: Up
Votes for Up: 3
Movie: Coco
Votes for Coco: 5
Movie: Cars
Votes for Cars: 2
Movie:
3 movies. Tonight we are watching Coco!
```

The program builds the list one dictionary at a time: `make_movie` returns a new dictionary, and append adds that whole dictionary to the end of the list. Then a loop over the list finds the winner.


### Answer

```python
def make_movie(title, votes):
    return {"title": title, "votes": votes}


def main():
    movies = []
    title = input("Movie: ")
    while title != "":
        votes = int(input(f"Votes for {title}: "))
        movies.append(make_movie(title, votes))
        title = input("Movie: ")
    if len(movies) == 0:
        print("No movies tonight!")
    else:
        winner = movies[0]
        for movie in movies:
            if movie["votes"] > winner["votes"]:
                winner = movie
        print(f"{len(movies)} movies. Tonight we are watching {winner['title']}!")


if __name__ == "__main__":
    main()
```
