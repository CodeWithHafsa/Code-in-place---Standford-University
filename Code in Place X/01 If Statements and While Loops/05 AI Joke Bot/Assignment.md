## Assignment
Write a program that tells jokes! Your program will greet the user, ask if they'd like to hear a joke, and then use AI to come up with one. As long as the user keeps saying "yes," your program should keep the jokes coming. When they finally say "no," the program ends.

Here's what a conversation with your finished program might look like:

```
Hello! I am an AI joke bot.
Do you want to hear a joke? Type yes or no: yes
Why did the scarecrow win an award?

Because he was outstanding in his field!

Do you want to hear a joke? Type yes or no: yes
Why don't skeletons fight each other?

They don't have the guts!

Do you want to hear a joke? Type yes or no: no
```

## MILESTONES

You don't have to build the whole thing at once. In fact, we'd encourage you not to! Here's one way to work up to it in small steps, testing your program as you go.


### Milestone 1: Tell a single joke. 

Have your program say hello, ask the user whether they want to hear a joke, and if they type "yes," generate one joke with `call_gpt` and print it out. Don't worry about repeating or looping yet, just get a single joke working from start to finish.

### Milestone 2: Keep telling jokes. 

Now bring in a while loop. After each joke, ask the user again whether they'd like another one. As long as they keep answering "yes," keep telling jokes; as soon as they type anything else, stop and let the program end.

### Milestone 3: Make different jokes.

Once Milestone 2 is working, you might notice something funny: the AI keeps telling you the same joke over and over. That's because it only knows what's in the prompt you give it, and your prompt hasn't changed. Your challenge is to fix this by telling the AI which jokes it has already told, so it knows to come up with something new each time.

Here's a hint: the AI can't remember anything on its own, but you can remind it. Try keeping track of the jokes so far and adding them into your prompt, so that the prompt grows a little each time through the loop. An f-string is a natural way to stitch your old prompt together with the newest joke to build the next one. Something along these lines can help:

```
gpt_prompt = f"{gpt_prompt}\nYou already told me: {joke}"
```

Give that a try, and see if your jokes start to vary. Good luck, and have fun!

---

### Code 

```python
def main():
    print("Hello! I am an AI joke bot.")

    gpt_prompt = "Tell me a funny joke. Give me only the joke, including the setup and punchline."

    while True:
        answer = input("Do you want to hear a joke? Type yes or no: ")

        if answer == "yes":
            joke = call_gpt(gpt_prompt)
            print(joke)
            print()

            gpt_prompt = f"{gpt_prompt}\nYou already told me: {joke}"
        else:
            break


if __name__ == "__main__":
    main()
```