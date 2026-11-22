## Chatbot

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

**The big idea:** An AI model has **no memory**. Every time you call call_gpt, it starts fresh. Chatbots seem to remember because the program keeps a list of every message, and sends the whole conversation every single time. You will build that list, and then you get to control it.

## Milestones

1. Goldfish Bot
2. Keep a Record
3. Peek at the Record
4. Give It a Memory
5. Give It a Personality
6. Rewind (optional)
7. Memory Budget (optional)
8. Compact (optional)

## Answer:

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