## Group Chat

Turn the chat into a group chat with two bots. Add this list to the top of your program, in place of PERSONALITY:

```python
BOTS = [
    {"name": "Captain Kit", "personality": "You are Captain Kit, a pirate in a group chat. Keep replies short."},
    {"name": "Chef Rosa", "personality": "You are Chef Rosa, a very dramatic chef in a group chat. Keep replies short."},
]
```

Start with an empty `messages` list. Each time the user sends a message, every bot replies in turn. Give each bot its own system message, glued onto the front of the shared conversation. Save each reply with the bot's name in front, so the bots can see who said what.

Here is a sample run (the AI's replies will be different):

```
Chat with the bots! (press Enter to quit)
You: My name is Sam.
Captain Kit: Arr! Nice to meet you, Sam!
Chef Rosa: Magnifique! Nice to meet you, Sam!
You: What's my name?
Captain Kit: Arr! Your name is Sam!
Chef Rosa: Magnifique! Your name is Sam!
You:
```


### Given Code:
```python
from ai import call_gpt

INDENT = "    "
PERSONALITY = "You are super sassy. Keep replies short."

def make_message(role, content):
    # Make a message like
    # {"role": "user", "content": "My name is Sam."}
    return {"role": role, "content": content}

def peek(messages):
    # Print how many messages are in the list,
    # then each message's role and content
    print(f"{INDENT}The record has {len(messages)} messages:")
    for message in messages:
        print(f"{INDENT}{message['role']}: {message['content']}")

def format_messages(messages):
    # Return a nicely formatted string version of the list
    result = ""
    for message in messages:
        if message["role"] == "user":
            result += f"User: {message['content']}\n"
        elif message["role"] == "system":
            result += f"Instructions: {message['content']}\n\n"
        else:
            result += f"Assistant: {message['content']}\n"
    result += "Assistant:"
    return result

def main():
    print("Chat with the bot! (press Enter to quit)")
    messages = [make_message("system", PERSONALITY)]

    # Prompt the user for the first message
    user_content = input("You: ")

    while user_content != "":
        if user_content == "peek":
            peek(messages)
        else:
            # Format and add the user message
            user_message = make_message("user", user_content)
            messages.append(user_message)

            # Get a response from the bot
            prompt = format_messages(messages)
            bot_content = call_gpt(prompt)
            print(f"Bot: {bot_content}")

            # Format and add the bot message
            bot_message = make_message("assistant", bot_content)
            messages.append(bot_message)

        # Get a new message from the user
        user_content = input("You: ")

if __name__ == "__main__":
    main()
```

#### What Changed?
1. Replace PERSONALITY with BOTS

```python
BOTS = [
    {"name": "Captain Kit", "personality": "You are Captain Kit, a pirate in a group chat. Keep replies short."},
    {"name": "Chef Rosa", "personality": "You are Chef Rosa, a very dramatic chef in a group chat. Keep replies short."},
]
```

2. Replace your `main()` function

```python
def main():
    print("Chat with the bots! (press Enter to quit)")
    messages = []

    user_content = input("You: ")

    while user_content != "":
        if user_content == "peek":
            peek(messages)
        else:
            # Add the user's message to the shared conversation
            user_message = make_message("user", user_content)
            messages.append(user_message)

            # Let each bot respond in turn
            for bot in BOTS:
                # Give each bot its own personality
                bot_messages = [make_message("system", bot["personality"])] + messages

                # Get the bot's response
                prompt = format_messages(bot_messages)
                bot_content = call_gpt(prompt)
                print(f"{bot['name']}: {bot_content}")

                # Save the reply with the bot's name
                bot_message = make_message("assistant", f"{bot['name']}: {bot_content}")
                messages.append(bot_message)

        user_content = input("You: ")
```

Three important things:

1. `messages = []` — Starts with an empty shared conversation.
2. `for bot in BOTS:` — Makes every bot respond to each user message.
3. `[make_message("system", bot["personality"])] + messages `— Gives each bot its own personality while keeping the shared conversation intact.

### Answer:

```python
from ai import call_gpt

INDENT = "    "
BOTS = [
    {"name": "Captain Kit", "personality": "You are Captain Kit, a pirate in a group chat. Keep replies short."},
    {"name": "Chef Rosa", "personality": "You are Chef Rosa, a very dramatic chef in a group chat. Keep replies short."},
]

def make_message(role, content):
    # Make a message like
    # {"role": "user", "content": "My name is Sam."}
    return {"role": role, "content": content}

def peek(messages):
    # Print how many messages are in the list,
    # then each message's role and content
    print(f"{INDENT}The record has {len(messages)} messages:")
    for message in messages:
        print(f"{INDENT}{message['role']}: {message['content']}")

def format_messages(messages):
    # Return a nicely formatted string version of the list
    result = ""
    for message in messages:
        if message["role"] == "user":
            result += f"User: {message['content']}\n"
        elif message["role"] == "system":
            result += f"Instructions: {message['content']}\n\n"
        else:
            result += f"Assistant: {message['content']}\n"
    result += "Assistant:"
    return result

def main():
    print("Chat with the bots! (press Enter to quit)")
    messages = []

    # Prompt the user for the first message
    user_content = input("You: ")

    while user_content != "":
        if user_content == "peek":
            peek(messages)
        else:
            # Format and add the user message
            user_message = make_message("user", user_content)
            messages.append(user_message)

            # Every bot replies, in order
            for bot in BOTS:
                system_message = make_message("system", bot["personality"])
                bot_messages = [system_message] + messages
                prompt = format_messages(bot_messages)
                bot_content = call_gpt(prompt)
                reply = f"{bot['name']}: {bot_content}"
                print(reply)
                bot_message = make_message("assistant", reply)
                messages.append(bot_message)

        # Get a new message from the user
        user_content = input("You: ")

if __name__ == "__main__":
    main()
```
