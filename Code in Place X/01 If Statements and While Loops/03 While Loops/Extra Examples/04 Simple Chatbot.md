## 04 Simple Chatbot
Write a simple chatbot program where a user can continually ask questions to the AI model. The user should be able to keep messaging the chatbot until they type bye to end the conversation.

Your program should:

1. Ask the user for a message.
2. As long as the message is **not** `bye`: send it to `call_gpt`, print the reply, and ask for another message.
3. When they type `bye`, print `Goodbye!`

Example output:
```
You: hello
AI: Hi there! How can I help?
You: What would you name a friendly dragon?
AI: I would name it Ember. It sounds warm and magical!
You: bye
Goodbye!
```

---
### Code

```python
from ai import call_gpt

def main():
    message = input("You: ")

    while message != "bye":
        response = call_gpt(message)
        print(f"AI: {response}")
        message = input("You: ")

    print("Goodbye!")

if __name__ == "__main__":
    main()
```