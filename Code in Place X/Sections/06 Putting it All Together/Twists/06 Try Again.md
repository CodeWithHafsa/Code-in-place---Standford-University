## Try Again

Add an `again` command that throws away the bot's last reply and asks for a new one, like the try again button on a real chatbot. Use a slice to remove the last message. If there is no reply yet, print `Nothing to try again yet`.

Here is a sample run (the AI's replies will be different):

```
Chat with the bot! (press Enter to quit)
You: again
    Nothing to try again yet.
You: Tell me a joke.
Bot: Ugh, fine. What do you call a sleeping bull? A bulldozer.
You: again
Bot: Ugh, fine. Why did the cookie cry? Its mom was a wafer so long.
You: peek
    The record has 3 messages:
    system: You are super sassy. Keep replies short.
    user: Tell me a joke.
    assistant: Ugh, fine. Why did the cookie cry? Its mom was a wafer so long.
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
Add an `again` command that removes the bot's last reply and generates a new one using the same user message.

1. Add this condition inside your `while` loop
Place it after the `if user_content == "peek":` condition:

```python
elif user_content == "again":
    if len(messages) < 3 or messages[-1]["role"] != "assistant":
        print(f"{INDENT}Nothing to try again yet.")
    else:
        messages = messages[:-1]
        prompt = format_messages(messages)
        bot_content = call_gpt(prompt)
        print(f"Bot: {bot_content}")

        bot_message = make_message("assistant", bot_content)
        messages.append(bot_message)
```

2. Updated loop

```python
while user_content != "":
    if user_content == "peek":
        peek(messages)

    elif user_content == "again":
        if len(messages) < 3 or messages[-1]["role"] != "assistant":
            print(f"{INDENT}Nothing to try again yet.")
        else:
            messages = messages[:-1]
            prompt = format_messages(messages)
            bot_content = call_gpt(prompt)
            print(f"Bot: {bot_content}")

            bot_message = make_message("assistant", bot_content)
            messages.append(bot_message)

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
        elif user_content == "again":
            if len(messages) < 3:
                print(f"{INDENT}Nothing to try again yet.")
            else:
                # Remove the bot's last reply and ask for a new one
                messages = messages[:len(messages) - 1]
                prompt = format_messages(messages)
                bot_content = call_gpt(prompt)
                print(f"Bot: {bot_content}")
                bot_message = make_message("assistant", bot_content)
                messages.append(bot_message)
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