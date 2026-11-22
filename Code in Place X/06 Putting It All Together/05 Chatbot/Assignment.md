## Chatbot

> About This Assignment

In this assignment you will build your own chatbot and discover how real chatbots like ChatGPT actually work.

Here is a sneak peek of the finished program. The bot remembers what you said, you can rewind the conversation, and when its memory fills up you get to choose what it forgets:

```
Chat with Pip! Type 'peek' to see its memory or 'rewind' to undo. (Enter to quit)
You: My name is Sam and my favorite color is teal.
Pip: Hi Sam, lovely to meet you! Stop by The Warm Crumb sometime, croissants are $3.
You: Tell me a bread pun.
Pip: Why did the baker win every argument? Because he always had the dough on his side!
You: rewind
    Rewound! The record has 3 messages.
You: Tell me a croissant pun.
Pip: Why did the croissant break up with the bagel? Things were getting a little too flaky!
...
You: What's my name and favorite color?
    My memory is full (181 words)! Type 'forget' or 'compact': compact
    Now I remember 3 messages, 89 words.
Pip: Your name is Sam, and your favorite color is teal!
```

**The big idea:** An AI model has **no memory**. Every time you call `call_gpt`, it starts fresh. Chatbots seem to remember because the program keeps a list of every message, and sends the whole conversation every single time. You will build that list, and then you get to control it.

----

### Milestone
#### Milestone 1 of 8
### Goldfish Bot

Start by printing `Chat with the bot! (press Enter to quit)`. Then write a chat loop in main. Ask the user for a message with `input("You: ")`, send it to `call_gpt`, and print the reply with `"Bot: "` in front. Stop when the user presses enter without typing anything.

Here is example output:
```
Chat with the bot! (press Enter to quit)
You: My name is Sam.
Bot: Hi Sam, nice to meet you! What can I help you with today?
You: What's my name?
Bot: I'm sorry, I don't know your name. Could you tell me?
```

**Try it:** tell the bot your name, then ask it what your name is. It has already forgotten! Like a goldfish, every call to `call_gpt` does not remember anything.

```python
from ai import call_gpt


def main():
    print("Chat with the bot! (press Enter to quit)")

    while True:
        message = input("You: ")

        if message == "":
            break

        response = call_gpt(message)
        print("Bot: " + response)


if __name__ == "__main__":
    main()
```

#### How it works

1. `print()` displays the welcome message.
2. `while True` keeps the conversation running.
3. `input("You: ")` gets a message from the user.
4. `if message == "":` checks whether the user pressed Enter without typing.
5. `break` exits the loop.
6. `call_gpt(message)` sends the message to the AI.
7. `print("Bot: " + response)` displays the reply.

----

#### Milestone 2 of 8
### Keep a Record
Save the conversation as a **list of dictionaries**, one per message. Each message has a role (who said it) and content (what they said). Here is an example of a conversation:

```python
messages = [
    {"role": "user", "content": "My name is Sam."},
    {"role": "assistant", "content": "Hi Sam, nice to meet you!"},
]
```

To implement this, follow these steps:

1. Write a function `make_message(role, content)` that returns one message dictionary.
2. In `main`, create an empty list called `messages`. 
3. Each time the user types a message, append a message to the list where the role is user. Each time the bot replies, append a message where the role is assistant.

After this milestone, your program output will not look any different than milestone 1.

```python
from ai import call_gpt
# Milestone 1: Goldfish Bot
# Milestone 2: Keep a Record

def make_message(role, content):
    return {
        "role": role,
        "content": content
    }


def main():
    print("Chat with the bot! (press Enter to quit)")

    messages = []

    while True:
        user_message = input("You: ")

        if user_message == "":
            break

        messages.append(make_message("user", user_message))

        response = call_gpt(user_message)

        messages.append(make_message("assistant", response))

        print("Bot: " + response)


if __name__ == "__main__":
    main()
```

#### What's new?
* `make_message(role, content)` – Creates a dictionary containing the speaker and their message.
* `messages = []` – Creates an empty conversation history.
* User message – Saves what the user types with the role `"user"`.
* Assistant message – Saves the bot's response with the role `"assistant"`.

---

#### Milestone 3 of 8
### Peek at the Record
Add a peek command that prints everything your program has saved in `messages`.

To implement this, follow these steps:

1. Make a constant `INDENT = "    "` (four spaces) at the top of your file.

2. Write a function `peek(messages)` that prints how many messages are in the list, then each message's role and content. Start every line it prints with `INDENT`, for example `print(f"{INDENT}The record has {len(messages)} messages:")`.

3. In `main`, when the user types peek, call `peek(messages)` instead of sending anything to `call_gpt`. Do not add `peek` to `messages`.

Here is example output of the program after this milestone:

```
Chat with the bot! (press Enter to quit)
You: My name is Sam.
Bot: Nice to meet you, Sam. How can I help you today?
You: What's my name?
Bot: I'm sorry, I don't know your name. Could you tell me?
You: peek
    The record has 4 messages:
    user: My name is Sam.
    assistant: Nice to meet you, Sam. How can I help you today?
    user: What's my name?
    assistant: I'm sorry, I don't know your name. Could you tell me?
```

<br>

```python

from ai import call_gpt

# Milestone 1: Goldfish Bot

INDENT = "    "

# Milestone 2: Keep a Record
def make_message(role, content):
    return {
        "role": role,
        "content": content
    }

# Milestone 3: Peek at Memory
def peek(messages):
    print(f"{INDENT}The record has {len(messages)} messages:")

    for message in messages:
        print(f"{INDENT}{message['role']}: {message['content']}")


def main():
    print("Chat with the bot! (press Enter to quit)")

    messages = []

    while True:
        user_message = input("You: ")

        if user_message == "":
            break

        if user_message == "peek":
            peek(messages)
            continue

        messages.append(make_message("user", user_message))

        response = call_gpt(user_message)

        messages.append(make_message("assistant", response))

        print("Bot: " + response)


if __name__ == "__main__":
    main()
```

#### What's new in Milestone 3?

- `INDENT` stores four spaces.
- `peek(messages)` displays the number of saved messages.
- The `for` loop prints each message's role and content.
- Typing `peek` displays memory without adding it to the conversation or sending it to GPT.

---

#### Milestone 4 of 8
### Give It a Memory
To give the bot a memory, send it the whole conversation every time, not just the newest message. Follow these steps:

1. Write a function `format_messages(messages)` that returns the conversation as one string. Put each message on its own line, starting with `"User: "` for user messages and `"Assistant: "` for the bot's messages. Then add `"Assistant:"` to the end of the string so the AI knows it is its turn to talk. For example, the function `format_messages` turns this list:
```python
[
    {"role": "user", "content": "My name is Sam."},
    {"role": "assistant", "content": "Nice to meet you, Sam."},
    {"role": "user", "content": "What's my name?"},
]
```
into this string:

```python
"User: My name is Sam.
Assistant: Nice to meet you, Sam.
User: What's my name?
Assistant:"
```

2. In `main`, after you append the user's message, add `prompt = format_messages(messages)` followed by `call_gpt(prompt)` to get the bot's response, instead of sending only the newest message. This way, you are passing the whole conversation to GPT.

Here is example output of your program after this milestone:

```
Chat with the bot! (press Enter to quit)
You: My name is Sam.
Bot: Nice to meet you, Sam. How can I help you today?
You: What's my name?
Bot: Your name is Sam!
```

<br>

```python
from ai import call_gpt

# Milestone 1: Goldfish Bot

INDENT = "    "

# Milestone 2: Keep a Record
def make_message(role, content):
    return {
        "role": role,
        "content": content
    }

# Milestone 3: Peek at Memory
def peek(messages):
    print(f"{INDENT}The record has {len(messages)} messages:")

    for message in messages:
        print(f"{INDENT}{message['role']}: {message['content']}")

# Milestone 4: Give It a Memory
def format_messages(messages):
    conversation = ""

    for message in messages:
        if message["role"] == "user":
            conversation += "User: " + message["content"] + "\n"
        else:
            conversation += "Assistant: " + message["content"] + "\n"

    conversation += "Assistant:"
    return conversation


def main():
    print("Chat with the bot! (press Enter to quit)")

    messages = []

    while True:
        user_message = input("You: ")

        if user_message == "":
            break

        if user_message == "peek":
            peek(messages)
            continue

        messages.append(make_message("user", user_message))

        prompt = format_messages(messages)
        response = call_gpt(prompt)

        messages.append(make_message("assistant", response))

        print("Bot: " + response)


if __name__ == "__main__":
    main()
```

#### What's new in Milestone 4?

- `format_messages(messages)` converts the conversation history into one string.
- Each user message starts with `User:`.
- Each bot message starts with `Assistant:`.
- The final `Assistant:` tells GPT it's time to respond.
- `call_gpt(prompt)` now receives the entire conversation instead of just the latest message.

Result: Your chatbot can now remember things you've said earlier in the conversation\!

---

#### Milestone 5 of 8
### Give It a Personality
A **system message** is a hidden first message that tells the AI who to be. The user never sees it. Use one to give your bot a personality:

1. Make a constant `PERSONALITY` with your bot's instructions: who it is, how it talks, and what it knows. Tell it to keep replies short.

2. In `main`, start `messages` with a system message instead of an empty list: `messages = [make_message("system", PERSONALITY)]`.

3. Update `format_messages` so a system message becomes `Instructions:`  plus its content, followed by a blank line (two \n).

For example, for a pirate bot, format_messages returns:

```
Instructions: You are a pirate.

User: Hi!
Assistant:
```

Here is the personality we used. Invent your own!

```python
PERSONALITY = "You are a super sassy queen. Keep replies short."
```

Here is example output:

```
Chat with the bot! (press Enter to quit)
You: How much is sourdough?
Bot: Depends on where you shop, darling! But don’t expect it to be cheap—artisan bread comes with a price! 💁‍♀️🥖
```

**Try it:** change one sentence of PERSONALITY and see how different your bot feels.

```python

from ai import call_gpt

# Milestone 1: Goldfish Bot

INDENT = "    "

# Milestone 2: Keep a Record
def make_message(role, content):
    return {
        "role": role,
        "content": content
    }


# Milestone 3: Peek at Memory
def peek(messages):
    print(f"{INDENT}The record has {len(messages)} messages:")

    for message in messages:
        print(f"{INDENT}{message['role']}: {message['content']}")


# Milestone 4: Give It a Memory
def format_messages(messages):
    conversation = ""

    for message in messages:
        if message["role"] == "system":
            conversation += "Instructions: " + message["content"] + "\n\n"
        elif message["role"] == "user":
            conversation += "User: " + message["content"] + "\n"
        else:
            conversation += "Assistant: " + message["content"] + "\n"

    conversation += "Assistant:"
    return conversation


# Milestone 5: Give It a Personality
PERSONALITY = "You are a super sassy queen. Keep replies short."


def main():
    print("Chat with the bot! (press Enter to quit)")

    messages = [make_message("system", PERSONALITY)]

    while True:
        user_message = input("You: ")

        if user_message == "":
            break

        if user_message == "peek":
            peek(messages)
            continue

        messages.append(make_message("user", user_message))

        prompt = format_messages(messages)
        response = call_gpt(prompt)

        messages.append(make_message("assistant", response))

        print("Bot: " + response)


if __name__ == "__main__":
    main()
```

#### What's new in Milestone 5?

1. `PERSONALITY` gives your chatbot its own character.
2. The system message is added when the conversation starts.
3. `format_messages()` displays system instructions as `Instructions:`.
4. Two `\n` characters create a blank line after the instructions.

---

#### Milestone 6 of 8 · Optional
### Rewind
When the user types `rewind`, remove the last exchange from `messages`, so the bot forgets it. An exchange is two messages: the user's message and the bot's reply.

To do this, you will use a **slice**. A slice makes a new list from part of a list. `my_list[:n]` gives every item before index n:

```python
letters = ["a", "b", "c", "d"]
first_two = letters[:2]
```

Now `first_two is ["a", "b"]`. The original list letters does not change.

Follow these steps:

1. Write a function `rewind(messages)` that returns a slice of `messages` without its last two messages. Hint: the slice should stop before index `len(messages) - 2`. If messages has fewer than 3 `messages`, there is nothing to rewind, so return `messages` unchanged. This keeps the system message safe.

2. In `main`, when the user types `rewind`, set `messages = rewind(messages)` instead of sending anything to call_gpt. You need the `messages =` part because a slice is a new list. `rewind` does not change the original list.

3. Then print how many messages are left, like `Rewound!` The record has `3 messages`. Start the line with INDENT.


For example, here is messages before a rewind:

```python
messages = [
    {"role": "system", "content": PERSONALITY},
    {"role": "user", "content": "My name is Sam."},
    {"role": "assistant", "content": "Nice to meet you, Sam!"},
    {"role": "user", "content": "Tell me a fun fact about octopuses."},
    {"role": "assistant", "content": "Octopuses have three hearts and blue blood!"},
]
```

`rewind(messages)` returns `messages[:3]`, which is everything except the last exchange:

```python
[
    {"role": "system", "content": PERSONALITY},
    {"role": "user", "content": "My name is Sam."},
    {"role": "assistant", "content": "Nice to meet you, Sam!"},
]
```

Here is example output of your program after this milestone:

```
Chat with the bot! (press Enter to quit)
You: My name is Sam.
Bot: Nice to meet you, Sam!
You: Tell me a fun fact about octopuses.
Bot: Octopuses have three hearts and blue blood!
You: rewind
    Rewound! The record has 3 messages.
You: Tell me a fun fact about otters.
Bot: Otters hold hands while they sleep so they don't drift apart.
You: What fun facts have you told me?
Bot: Just one so far: otters hold hands while they sleep!
```

**Try it:** ask for a fun fact, type rewind, ask for a different one, and then ask the bot which facts it has told you.

```python

from ai import call_gpt

# Milestone 1: Goldfish Bot

INDENT = "    "

# Milestone 2: Keep a Record
def make_message(role, content):
    return {
        "role": role,
        "content": content
    }


# Milestone 3: Peek at Memory
def peek(messages):
    print(f"{INDENT}The record has {len(messages)} messages:")

    for message in messages:
        print(f"{INDENT}{message['role']}: {message['content']}")


# Milestone 4: Give It a Memory
def format_messages(messages):
    conversation = ""

    for message in messages:
        if message["role"] == "system":
            conversation += "Instructions: " + message["content"] + "\n\n"
        elif message["role"] == "user":
            conversation += "User: " + message["content"] + "\n"
        else:
            conversation += "Assistant: " + message["content"] + "\n"

    conversation += "Assistant:"
    return conversation


# Milestone 5: Give It a Personality
PERSONALITY = "You are a super sassy queen. Keep replies short."


# Milestone 6: Rewind
def rewind(messages):
    if len(messages) < 3:
        return messages

    return messages[:len(messages) - 2]


def main():
    print("Chat with the bot! (press Enter to quit)")

    messages = [make_message("system", PERSONALITY)]

    while True:
        user_message = input("You: ")

        if user_message == "":
            break

        if user_message == "peek":
            peek(messages)
            continue

        if user_message == "rewind":
            messages = rewind(messages)
            print(f"{INDENT}Rewound! The record has {len(messages)} messages.")
            continue

        messages.append(make_message("user", user_message))

        prompt = format_messages(messages)
        response = call_gpt(prompt)

        messages.append(make_message("assistant", response))

        print("Bot: " + response)


if __name__ == "__main__":
    main()
```

#### What's new in Milestone 6?
* `rewind(messages)` removes the last two messages (one user message and one assistant reply).
* `messages[:len(messages) - 2]` creates a new list without the last exchange.
* `if len(messages) < 3` protects the system message.
* `messages = rewind(messages)` updates the conversation history.
* `continue` prevents `rewind` from being sent to GPT.

---


#### Milestone 7 of 8 · Optional
### Memory Budget
AI models can only read so much text at once. Give your bot a memory budget: when the conversation gets too long, it forgets the oldest messages.

Follow these steps:

1. Make a constant `MAX_WORDS = 150`. Write a function `count_words(messages)` that returns the total number of words in the content of every message, including the system message. **Hint:** `len(text.split())` counts the words in `text`.

2. Write a function `forget(messages)` that returns a new list with the system message, followed by everything after the 4 oldest messages. The system message is at index 0 and the 4 oldest messages are at indices 1 to 4, so join `messages[:1]` with a slice that starts at index 5. **Hint:** `my_list[n:]` gives every item from index n to the end, and + joins two lists. If `messages` has fewer than 6 messages, return it unchanged.

3. In `main`, after you append the user's message, check whether `count_words(messages)` is more than `MAX_WORDS`. If it is, set `messages = forget(messages)` and print how many messages and words are left, like My memory was full! Now I remember 6 messages, 116 words. Start the line with INDENT.

For example, if `messages` is `[system, m1, m2, m3, m4, m5, m6], then forget(messages) returns [system, m5, m6].`

Here is example output of your program after this milestone:

```
You: What's my name and favorite color?
    My memory was full! Now I remember 6 messages, 116 words.
Bot: I don't know your name or favorite color yet, dough-friend!
```

**Try it:** tell your bot your name and favorite color, chat until its memory fills up, and then ask about them.

```python

from ai import call_gpt

# Milestone 1: Goldfish Bot

INDENT = "    "

# Milestone 2: Keep a Record
def make_message(role, content):
    return {
        "role": role,
        "content": content
    }


# Milestone 3: Peek at Memory
def peek(messages):
    print(f"{INDENT}The record has {len(messages)} messages:")

    for message in messages:
        print(f"{INDENT}{message['role']}: {message['content']}")


# Milestone 4: Give It a Memory
def format_messages(messages):
    conversation = ""

    for message in messages:
        if message["role"] == "system":
            conversation += "Instructions: " + message["content"] + "\n\n"
        elif message["role"] == "user":
            conversation += "User: " + message["content"] + "\n"
        else:
            conversation += "Assistant: " + message["content"] + "\n"

    conversation += "Assistant:"
    return conversation


# Milestone 5: Give It a Personality
PERSONALITY = "You are a super sassy queen. Keep replies short."


# Milestone 6: Rewind
def rewind(messages):
    if len(messages) < 3:
        return messages

    return messages[:len(messages) - 2]


# Milestone 7: Memory Budget
MAX_WORDS = 150


def count_words(messages):
    total = 0

    for message in messages:
        total += len(message["content"].split())

    return total


def forget(messages):
    if len(messages) < 6:
        return messages

    return messages[:1] + messages[5:]


def main():
    print("Chat with the bot! (press Enter to quit)")

    messages = [make_message("system", PERSONALITY)]

    while True:
        user_message = input("You: ")

        if user_message == "":
            break

        if user_message == "peek":
            peek(messages)
            continue

        if user_message == "rewind":
            messages = rewind(messages)
            print(f"{INDENT}Rewound! The record has {len(messages)} messages.")
            continue

        messages.append(make_message("user", user_message))

        if count_words(messages) > MAX_WORDS:
            messages = forget(messages)
            print(
                f"{INDENT}My memory was full! Now I remember "
                f"{len(messages)} messages, {count_words(messages)} words."
            )

        prompt = format_messages(messages)
        response = call_gpt(prompt)

        messages.append(make_message("assistant", response))

        print("Bot: " + response)


if __name__ == "__main__":
    main()
```

#### What's new in Milestone 7?
* `MAX_WORDS = 150` sets the memory limit.
* `count_words(messages)` counts all words in the conversation, including personality instructions.
* `forget(messages)` keeps the system message and removes the four oldest conversation messages.
* The memory check happens after adding the user's message.
* The bot prints how many messages and words remain after forgetting.

---

#### Milestone 8 of 8 · Optional
### Compact
When your bot forgets, everything in the old messages is lost. Real chatbots often **compact** instead: they ask the AI to summarize the old messages, and keep only the summary.

Follow these steps:
1. Write a function `compact(messages`). If `messages` has fewer than 3 messages, there is nothing to summarize, so return it unchanged.

2. Get the old messages: every message except the first (the system message) and the last (the newest message). Use the slice `messages[1:len(messages) - 1]. my_list[a:b]` gives the items from index a up to, but not including, index b.

3. Ask `call_gpt` to summarize the old messages. Send it an instruction like `"Summarize this conversation in two or three sentences. Keep names and anything the user said about themselves."` followed by `format_messages` of the old messages.

4. Return a new list with three messages: the system message, a new system message whose content is `Summary of the conversation so far:`  followed by the summary, and the newest message.

5. In `main`, when the memory is full, ask the user to type `forget` or `compact`, as shown below. If they type `compact`, set `messages = compact(messages)`. Otherwise, set messages = forget(messages). Then print how many messages and words are left, starting with `INDENT`.

Here is example output of your program after this milestone:

```
You: What's my name and favorite color?
    My memory is full (181 words)! Type 'forget' or 'compact': forget
    Now I remember 6 messages, 116 words.
Bot: I don't know your name or favorite color yet, dough-friend!
```

```
You: What's my name and favorite color?
    My memory is full (181 words)! Type 'forget' or 'compact': compact
    Now I remember 3 messages, 89 words.
Bot: Your name is Sam, and your favorite color is teal!
```

**Try it:** tell your bot your name and favorite color, chat until its memory fills up, and then ask about them. Try once with `forget` and once with compact. Then keep chatting and `compact` a few times in a row. What survives a summary of a summary?

#### What's new in Milestone 8?
* `compact(messages)` collects the older conversation.
* `call_gpt()` summarizes the old messages in two or three sentences.
* The original system personality is preserved.
* A new system message stores the summary.
* The newest user message is preserved.
* When memory fills up, the user chooses `forget` or `compact`.

## Final Answer

```python

from ai import call_gpt

# Milestone 1: Goldfish Bot

INDENT = "    "

# Milestone 2: Keep a Record
def make_message(role, content):
    return {
        "role": role,
        "content": content
    }


# Milestone 3: Peek at Memory
def peek(messages):
    print(f"{INDENT}The record has {len(messages)} messages:")

    for message in messages:
        print(f"{INDENT}{message['role']}: {message['content']}")


# Milestone 4: Give It a Memory
def format_messages(messages):
    conversation = ""

    for message in messages:
        if message["role"] == "system":
            conversation += "Instructions: " + message["content"] + "\n\n"
        elif message["role"] == "user":
            conversation += "User: " + message["content"] + "\n"
        else:
            conversation += "Assistant: " + message["content"] + "\n"

    conversation += "Assistant:"
    return conversation


# Milestone 5: Give It a Personality
PERSONALITY = "You are a super sassy queen. Keep replies short."


# Milestone 6: Rewind
def rewind(messages):
    if len(messages) < 3:
        return messages

    return messages[:len(messages) - 2]


# Milestone 7: Memory Budget
MAX_WORDS = 150


def count_words(messages):
    total = 0

    for message in messages:
        total += len(message["content"].split())

    return total


def forget(messages):
    if len(messages) < 6:
        return messages

    return messages[:1] + messages[5:]


# Milestone 8: Compact
def compact(messages):
    if len(messages) < 3:
        return messages

    old_messages = messages[1:len(messages) - 1]

    summary_prompt = (
        "Summarize this conversation in two or three sentences. "
        "Keep names and anything the user said about themselves.\n\n"
        + format_messages(old_messages)
    )

    summary = call_gpt(summary_prompt)

    return [
        messages[0],
        make_message(
            "system",
            "Summary of the conversation so far: " + summary
        ),
        messages[-1]
    ]


def main():
    print("Chat with the bot! (press Enter to quit)")

    messages = [make_message("system", PERSONALITY)]

    while True:
        user_message = input("You: ")

        if user_message == "":
            break

        if user_message == "peek":
            peek(messages)
            continue

        if user_message == "rewind":
            messages = rewind(messages)
            print(f"{INDENT}Rewound! The record has {len(messages)} messages.")
            continue

        messages.append(make_message("user", user_message))

        if count_words(messages) > MAX_WORDS:
            choice = input(
                f"{INDENT}My memory is full ({count_words(messages)} words)! "
                "Type 'forget' or 'compact': "
            )

            if choice == "compact":
                messages = compact(messages)
            else:
                messages = forget(messages)

            print(
                f"{INDENT}Now I remember {len(messages)} messages, "
                f"{count_words(messages)} words."
            )

        prompt = format_messages(messages)
        response = call_gpt(prompt)

        messages.append(make_message("assistant", response))

        print("Bot: " + response)


if __name__ == "__main__":
    main()
```