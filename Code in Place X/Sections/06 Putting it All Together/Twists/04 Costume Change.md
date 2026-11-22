## Costume Change

Add a `costume` command that asks for a new personality and gives the bot that personality, without forgetting the conversation. Replace the old system message with a new one, but keep every message after it. To do this, make a new system message and glue it onto everything after the old system message.

Here is a sample run (the AI's replies will be different):

```
Chat with the bot! (press Enter to quit)
You: My name is Sam.
Bot: Ugh, fine. Nice to meet you, Sam!
You: costume
New personality: You are a pirate. Keep replies short.
    Costume changed!
You: What's my name?
Bot: Arr! Your name is Sam!
You: peek
    The record has 5 messages:
    system: You are a pirate. Keep replies short.
    user: My name is Sam.
    assistant: Ugh, fine. Nice to meet you, Sam!
    user: What's my name?
    assistant: Arr! Your name is Sam!
You:
```

### Given Code

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

#### What changed?
Add a `costume` command that replaces the system message while keeping the rest of the conversation.

1. Add this condition inside your `while` loop
Place it after the `if user_content == "peek":` condition:

```python
elif user_content == "costume":
    new_personality = input("New personality: ")
    new_system_message = make_message("system", new_personality)
    messages = [new_system_message] + messages[1:]
    print(f"{INDENT}Costume changed!")
```

2. How does it work?
The important line is:

```
messages = [new_system_message] + messages[1:]
```

3. Updated loop

```python
while user_content != "":
    if user_content == "peek":
        peek(messages)
    elif user_content == "costume":
        new_personality = input("New personality: ")
        new_system_message = make_message("system", new_personality)
        messages = [new_system_message] + messages[1:]
        print(f"{INDENT}Costume changed!")
    else:
        user_message = make_message("user", user_content)
        messages.append(user_message)

        prompt = format_messages(messages)
        bot_content = call_gpt(prompt)
        print(f"Bot: {bot_content}")

        bot_message = make_message("assistant", bot_content)
        messages.append(bot_message)

    user_content = input("You: ")
```

### Answer

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
        elif user_content == "costume":
            personality = input("New personality: ")
            system_message = make_message("system", personality)
            messages = [system_message] + messages[1:]
            print(f"{INDENT}Costume changed!")
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