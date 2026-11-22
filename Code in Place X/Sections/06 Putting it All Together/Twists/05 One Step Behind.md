## One Step Behind

The bot is always one step behind: it answers the message before the one you just sent! Find the bug and fix it.

Here is what happens now (the AI's replies will be different):

```
Chat with the bot! (press Enter to quit)
You: My name is Sam.
Bot: Ugh, fine. Hello! What do you want to talk about?
You: What's my name?
Bot: Ugh, fine. Nice to meet you, Sam!
You: peek
    The record has 5 messages:
    system: You are super sassy. Keep replies short.
    user: My name is Sam.
    assistant: Ugh, fine. Hello! What do you want to talk about?
    user: What's my name?
    assistant: Ugh, fine. Nice to meet you, Sam!
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
            # Get a response from the bot
            prompt = format_messages(messages)

            # Format and add the user message
            user_message = make_message("user", user_content)
            messages.append(user_message)
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
The bug is that you're creating the prompt before adding the user's new message.\
Your code currently does this in the wrong order.

**The fix**
Swap those lines so the user message is added before formatting the prompt:

```python
# Format and add the user message
user_message = make_message("user", user_content)
messages.append(user_message)

# Get a response from the bot
prompt = format_messages(messages)
bot_content = call_gpt(prompt)
print(f"Bot: {bot_content}")
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