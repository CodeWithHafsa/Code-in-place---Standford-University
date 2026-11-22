## Build an Agent

Overview
In the chatbot assignment you built a bot that remembers what you've been talking about. This time you'll build one that can act. Ask it to change something in your program, and your program will actually do it!

A Large Language Model (LLM), like the one you've been using in call_gpt, can't run your code. What it can do is ask, in a message your program reads, for something to happen. Your program can then run some pre-written code to produce a result, and send that result back to the model to process.

Each capability exposed to the model like this is called a tool. Broadly speaking, a **tool** is a function in your program that gives the model a new ability: a way to change something in your program (for example, changing the value of a variable). It's important to remember that the model never runs a tool itself. It asks, and your program does the work and reports back to the model. A program that gives an LLM tools like this is called an **agent**.

By the end, you'll have one loop that can run any agent you can think of, built from nothing but a prompt and a dictionary of tools.

Watch this first: in the [Beyond CIPX lesson](https://codeinplace.stanford.edu/cipx/learn/beyond-cipx), Brahm, one of the original creators of Code in Place, walks through how agents work.

#### How to work through this
This assignment starts where the last one ended: your finished chatbot from the week 6 Chatbot assignment is your starter code. You'll copy it onto your computer in milestone 1. There are eight milestones, and each one gives your agent a new ability. Run your program after every milestone.

1. **Build call_gpt.** You write the function that talks to the model, using your own API key, and bring in your chatbot.
2. **Give It Hands.** The bot can add a task to a list.
3. **Let It Look.** The bot can read the list back to you.
4. **Let It Plan.** The bot can cross tasks off, working out the steps on its own.
5. **Speak Dictionary.** The same abilities, with a sturdier way to ask for them.
6. **Give Tasks a Priority.** Tasks carry more information, and the bot can use it.
7. **Keep It Safe.** The bot recovers from mistakes and can't run away.
8. **Swap the Tools.** One loop runs any agent you give it, like a finance tracker.

### Before You Start: Get Set Up
This assignment runs on your own computer, not in the Code in Place editor. Before milestone 1:

1. **Install Python and VS Code** by following the [setup guide](https://codeinplace.stanford.edu/cipx/build-an-agent/setup), Setting Up Python and VS Code (Windows & Mac).

2. **Download the starter code** with the **Starter code** button at the top right of this page, and unzip it somewhere you'll find it again, like your Desktop or Documents folder. After unzipping, the folder looks like this:

```
build-an-agent/
    README.txt
    ai.py
    main.py
    notopenai/
        __init__.py
        cacert.pem
        cacert-LICENSE.txt
```

* `ai.py` is where you write `call_gpt` in milestone 1.
* `main.py` is a placeholder. You'll paste your chatbot over it in milestone 1.
* `notopenai/` is the library that talks to the AI model. You never need to open or edit it.

3. **Open the folder in VS Code.** Choose **File → Open Folder** (on a Mac, **File → Open**) and pick the unzipped folder itself: not the zip, and not a folder inside it. You should see `ai.py`, `main.py` and `notopenai` in VS Code's sidebar.

4. **Get your API key.** That's the first step of milestone 1, below.

There's nothing to install with pip. Everything the starter code needs comes with Python.

## Milestone 1: Build call_gpt
You've used `call_gpt` throughout the class, but it only exists because Code in Place gives it to you. Out in the real world there is (unfortunately!) no `call_gpt` to import. If we want our programs to talk to AI models, we have to write that code ourselves.

Two ideas make it work. An **API key** is a password that tells an AI service who you are, so it knows whose requests to answer and how much you've used. A **library** is code someone else wrote that you import and use, without needing to know how it works inside. Here, the `notopenai` library handles sending your request and bringing back the reply.

### Get your key
Real AI services charge for every request, so a program has to say who it is each time it asks. Your key does that: every time your program asks the model something, it sends the key along. The Code in Place server checks whose key it is and how much they've used, then passes the message on to the model.

Code in Place gives you your own key for free, so you don't need an OpenAI account or a credit card. Keys are only available to students in the course. It starts with `noai`-. It isn't an OpenAI key: it only works with the `notopenai` library in your starter code.

1. Sign in to [codeinplace.stanford.edu](https://codeinplace.stanford.edu/) with the account you use for Code in Place.

2. Go to [codeinplace.stanford.edu/cipx/build-an-agent/key](https://codeinplace.stanford.edu/cipx/build-an-agent/key) (or click the **Your API key** tab at the top of this page).

3. Your key is hidden. Click **Show** to see it, or the copy button to copy it.

4. Paste it between the quotes in `ai.py`, in place of `noai-`...:

```python
API_KEY = "noai-..."
```

If the page says you don't have a key yet, check that you're signed in with the same account you use for the course. If you are and still have no key, fill out the [report form](https://codeinplace.stanford.edu/cipx/report).

Your key comes with some limits, so a program with a bug can't use up everything at once:

* **2,000,000 tokens in total**, for the whole assignment. They never reset. Tokens are the pieces of text the model reads and writes, roughly three-quarters of a word each. A long conversation with your finished agent uses about 20,000, so you have plenty.
* **30 requests a minute**, and **500 a day**. The daily count starts over at midnight UTC.
* **64,000 characters** of conversation in one request. Restarting your program starts a fresh, short conversation.

To see how many tokens you have left, run this in the terminal, from your project folder, once you've finished this milestone:

```
python3 -c "import ai; print(ai.client.usage())"
```

(On Windows, use `python` instead of `python3`.)

### Write call_gpt
Read how the library's own example uses it:

```python
from notopenai import NotOpenAI

client = NotOpenAI(api_key="noai-...")
response = client.responses.create(model="gpt-5-nano", input="Hello!")
print(response.output_text)
```

Now turn that into `call_gpt`:

* Put your key in a constant called `API_KEY` at the top of `ai.py`. Paste it between the quotes, in place of `noai-`....
* Create the client once, at the top of the file, with `NotOpenAI(api_key=API_KEY)`.
* Write `call_gpt(prompt)`. It sends prompt to the model `"gpt-5-nano"` and returns the reply's `output_text`.

Test it by adding this line to the bottom of ai.py, running the file, and deleting the line once it works:

```python
print(call_gpt("Say hello in one sentence."))
```

Example output:

```
Hello! It's great to meet you.
```

Your reply will be worded differently, because the model produces fresh text every time.

**Careful with your key.** Treat it like a password: don't post it, and don't share code that has it in it. Your key lives only in ai.py, so you can share main.py when you ask for help without giving your key away. If you think someone else has your key, or it stops working, fill out the report form and we'll send you a new one.

### Bring in your chatbot
Your finished program from the week 6 **Chatbot** assignment is the starting point for everything that follows. It lives in the Code in Place editor, so copy it over:

1. Open the [Chatbot assignment](https://codeinplace.stanford.edu/cipx/ide/a/chatbot) in Code in Place.
2. Click in `main.py`, select all of it (Ctrl+A on Windows, Cmd+A on a Mac), and copy it.
3. In VS Code, open `main.py` from the starter code, select everything in it, and paste your chatbot over it.

The milestones ahead build on these pieces of it:

* `INDENT`, which the program uses to set its own messages apart.
* `PERSONALITY`, your bot's system message.
* `make_message(role, content)`, which builds one message dictionary.
* f`ormat_messages(messages)`, which turns the list of messages into the text sent to call_gpt.
* `main()`, your chat loop. You'll keep changing it in every milestone.

Your agent doesn't need the chatbot's other features: `peek`, `rewind` and the memory budget (`MAX_WORDS`, `count_words`, `forget` and `compact`). Delete those functions, and the parts of `main` that use them, so your loop just reads a message, calls `call_gpt` and prints the reply. The agent's instructions get long, so a 150-word memory budget would fill up on almost every message.

Keep the first line, `from ai import call_gpt`. In the Code in Place editor, `ai.py` was provided for you. Now it's the file you just wrote.

Don't have a finished chatbot? Get it working first: it needs at least *Give It a Memory and Give It a Personality*, so that it keeps a list of messages and has a `PERSONALITY`.

Now for the payoff. Your chatbot imports `call_gpt` from `ai.py`, so it should work with the function you just wrote. Run your chatbot (`main.py`) and have a conversation. In VS Code, open main.py and click the Run button (▷) in the top right, or run `python3` `main.py` in the terminal (`python main.py` on Windows).

#### Example output:

```
You: What's the capital of France?
Bot: Paris.
Your bot's replies will use its own name and personality.
```

**Try it:** tell your bot your name, then ask what it is. It still remembers, and every message it sends now goes through the function you just wrote.

## Milestone 2: Give It Hands
The AI can't change anything in your program by itself: it can't see your variables, or read your code. It runs on a computer far away, and all it ever sends back is text. Your program has to read that text, spot the command, and do the work. This also means the bot can only do what your code lets it do.

Add an empty list called `todos` at the top of your file. It will hold your tasks, as plain strings. Then make a new constant called `TOOL_CALLS`, next to your `PERSONALITY`, with these lines:

```
You can add tasks to the user's to-do list. When the user wants to add one, reply with exactly this and nothing else:
ADD: <the task>
For anything else, just talk normally.
```

In the Give It a Personality milestone, you set up your bot's system message (the hidden instructions that tell the bot who to be). Now it's both constants, one after the other: `make_message("system", PERSONALITY + "\n" + TOOL_CALLS`).

They do different jobs. `PERSONALITY` says who the bot is. `TOOL_CALLS` says how it asks your program to do things. The bot has no idea your program exists, and your program only understands one exact format, so `TOOL_CALLS` spells that format out. It says "exactly this and nothing else" because any extra words would stop your code from recognizing the command. Keeping the two apart means you can change one without touching the other.

Then change your program so that:

* Write a function, `add_todo(task)`, that adds the task to `todos` and returns `"Added: "` followed by the task. This is your bot's first tool: a function your program runs when the bot asks.
* If the reply starts with `"ADD: "`, everything after it is a task. Call `add_todo` with the task.
* Print [`tool call`] followed by the reply, then the string `add_todo` returned, both with `INDENT` in front.
* Any other reply is printed like before, but with `"Agent: "` in front instead of your bot's name.

Example output:

```
You: add buy milk to my list
    [tool call] ADD: buy milk
    Added: buy milk
```

**Try it:** add three tasks and watch the `Added:` lines. Then ask the bot something that isn't a task, like *what's the capital of France?*, and check that it just answers. This is the first thing your bot has done that isn't talking. If you ever see it write extra words before `ADD:`, your program won't notice. Hold on to that thought for milestone 5.

## Milestone 3: Let It Look
Your bot can add tasks, but it can't tell you what's on the list. It never finds out what happened after it sends a command. Let's fix that.

Keep one thing in mind: the bot can't see your `todos` list. When your program runs `LIST`, all it has is a string. The bot only learns what's on the list if your program sends it that string, as one more message, and calls the bot again. The bot reads it like anything else it's sent. From here on, results all travel this way: your program runs the command, saves the result in `messages`, and calls the bot again.

Add these lines to the end of `TOOL_CALLS`:

```
To see the user's list, reply with exactly: LIST
Add one task per command: if the user lists several tasks, send ADD once for each.
Send one command at a time, then stop. You will be shown the result and can reply again.
Do not repeat a command you have already sent for the same request.
```

The first line is the new command. The other three tell the bot how to work in steps, now that it will see the result of each command.

Then change your program so that:

* Write a second tool, `list_todos()`, that returns a string with the numbered tasks, one per line, or `"The list is empty."` if there are none. A reply of exactly `"LIST"` calls it.
* After any command runs, its result is saved in `messages` with the role `"tool"`. For `ADD:` the result is `"Added: "` followed by the task.
* `format_messages` shows a `"tool"` message as `"Tool result: "` followed by its content. That's one more `elif`, and it goes before the `else`, because the else catches every role it hasn't checked yet.
* `format_messages` puts each message on its own line: end each one with `"\n"` instead of a space, and the system message with `"\n\n"`. The bot keeps track of what it has already done much better this way.
* The bot is called again after every command, so it can read the result. It might need several in a row, so put that call inside a second while loop and keep going until the bot sends a reply that isn't a command. Print that reply with `"Agent: "` in front.
* Use a variable to say whether the bot is still working: set `is_working = True` before the inner loop, loop `while is_working:`, and set it to `False` once the bot answers you. (If you know break, you can use it instead: it ends the loop on the spot.)
* Add a constant `MAX_TOOL_CALLS = 5`, and count the commands the bot sends for one message from you. When it hits the limit, print `Too many tool calls, so I stopped.` with `INDENT` in front and set `is_working` to `False`, so you're back at `You:` . Reset the count to 0 for every message you type, not once at the top of `main`.

After an `ADD:`, `messages` looks like this. The result is a dictionary like every other message, with the role `"tool"`:

```
[
  {"role": "system", "content": "...your PERSONALITY and TOOL_CALLS..."},
  {"role": "user", "content": "add buy milk"},
  {"role": "assistant", "content": "ADD: buy milk"},
  {"role": "tool", "content": "Added: buy milk"}
]
```

`format_messages` turns that list into the text the bot reads on its next turn:

```
Instructions: ...your PERSONALITY and TOOL_CALLS...

User: add buy milk
Assistant: ADD: buy milk
Tool result: Added: buy milk
Assistant:
```

The bot reads the result like any other line, and writes what comes next.

Example output:

```
You: add milk and eggs, then show me my list
    [tool call] ADD: milk
    [tool call] ADD: eggs
    [tool call] LIST
Agent: Done! Your list is 1. milk, 2. eggs.
```

**Try it:** ask the bot what's on your list. The [`tool call`] line shows it asking for `LIST`, and its answer comes from the result your program sent back.

**Your bot will sometimes get stuck.** The model we use is small, and with plain-text commands it often sends the same command again, like `LIST` five times in a row, instead of answering. That isn't a bug in your code. `MAX_TOOL_CALLS` is what stops it, which is exactly why you added it. Milestone 5 gives the bot a sturdier way to ask, and it gets much steadier.

## Milestone 4: Let It Plan
Now your bot learns to cross things off, and it will have to work out how.

It's called Let It Plan because crossing a task off takes two steps. The bot has to find the task's number with `LIST`, and then send `DONE:`. Nobody tells it to do them in that order. Working out the steps is the planning.

Add a third command to `TOOL_CALLS`:

```
To cross a task off the list, reply with exactly: DONE: <the task number>
```


Write a third tool, `complete_todo(number)`. It crosses off the task with that number by removing it from `todos` with pop, and returns `"Completed: "` followed by the task, or `"There is no task with that number."` A reply starting with `"DONE: "` calls it. Save what it returns in `messages` like the other commands.

Example output:

```
You: add milk and eggs
    [tool call] ADD: milk
    [tool call] ADD: eggs
Agent: Added both!
You: I bought the milk
    [tool call] LIST
    [tool call] DONE: 1
Agent: Nice, milk is crossed off.
```

**Mind the numbering.** People count tasks from 1, but lists count from 0, so task number 1 is `todos[0]`. Also, `reply[6:]` is a string, so turn it into a number with `int` before you use it.

**Try it:** add a few tasks, then say you finished one without giving its number, like *I bought the milk*. Look at the tool calls. Your code never says "look up the number first". The bot worked that out. If it guesses a number without listing first and crosses off the wrong task, add a line to `TOOL_CALLS` telling it to use `LIST` before `DONE:`. Our small model does this often, so you'll probably need that line. Either way, your bot now decides for itself when to use a tool, runs it, and reads the result. That's an agent!

## Milestone 5: Speak Dictionary
Look at your command code. It has `reply[:5] == "ADD: "` and `reply[5:]`, then `reply[:6]` and `reply[6:]`. Those numbers are character counts. Rename `ADD` to `ADD_TASK` and every one of them breaks without an error.

Dictionaries fix this. Instead of asking where in the reply a value sits, you ask for it by name.

Replace the three commands in `TOOL_CALLS` with this:

```
Reply with exactly one JSON dictionary, with no other text.
To talk to the user: {"type": "response_to_human", "message": "..."}
To use a tool: {"type": "tool_call_request", "tool_name": "...", "tool_argument": "..."}
Tools:
add_todo, argument: the task
list_todos, argument: ""
complete_todo, argument: the task number
Before using complete_todo, use list_todos to check the task number.
Add one task per tool call: if the user lists several tasks, call add_todo once for each.
Request one tool at a time, then stop. You will be shown the result and can reply again.
Do not repeat a tool call you have already made for the same request.
```

The last four lines do the same jobs as before, reworded for tools.

Then change your program so that it:

* Starts with `import json` at the top of the file.
* Turns the bot's reply text into a dictionary with `json.loads`.
* Checks `reply["type"]`. For `"response_to_human"`, it prints `reply["message"]` with `"Agent: "` in front.
* For `"tool_call_request"`, it reads `reply["tool_name"]` and `reply["tool_argument"]`, prints both after [`tool call`], and uses `if` and `elif` on the tool name to call the right tool function. For `complete_todo`, turn the argument into a number with int first.

Then delete your slicing code. There shouldn't be a 5 or a 6 left.

Example output:

```
You: add buy milk to my list
    [tool call] add_todo buy milk
Agent: Added buy milk to your list.
```

The bot can do exactly what it could before. What changed is your code: it reads values by name, not by position. `json.loads` is the one new function. It turns a string that looks like a dictionary into a real dictionary.

**Watch what you save in messages.** It should be the bot's raw reply text, not the dictionary. If you save the dictionary, `format_messages` crashes when it tries to add it to a string.

**Try it:** ask politely, like *could you please add milk to my list? thanks!*, and check that it still works. Then compare your code with milestone 4 and count how many numbers you got to delete. You should also see the bot get stuck much less often than it did with plain-text commands.

## Milestone 6: Give Tasks a Priority
Your bot speaks dictionary now, so it can send more than one value at a time. It just needs a dictionary of its own to hold them.

In the bot's replies, change `"tool_argument": "..."` to `"tool_parameters": {...}`. Update the tool list in `TOOL_CALLS` to match:

```
add_todo, parameters: {"task": "...", "priority": "high" or "low"}
list_todos, parameters: {}
complete_todo, parameters: {"number": 1}
```

Then change your program so that:

* Each tool function now takes one dictionary, `parameters`, instead of separate arguments: `add_todo(parameters)`, `list_todos(parameters)` and `complete_todo(parameters)`. They still return the result string. Your `if` and `elif` call them with `reply["tool_parameters"]`.
* Each task in `todos` is a dictionary, like `{"task": "buy milk", "priority": "high"}`, not a string.
* `list_todos` shows the priority after each task, like `1`. `buy milk (high)`.

Example output:

```
You: add buy milk, high priority
    [tool call] add_todo {'task': 'buy milk', 'priority': 'high'}
Agent: Added buy milk as a high priority.
You: add call mom, low priority
    [tool call] add_todo {'task': 'call mom', 'priority': 'low'}
Agent: Added call mom as a low priority.
You: what should I do first?
    [tool call] list_todos {}
Agent: Start with buy milk. It's high priority.
```

`pop` gives you back the whole dictionary now, so when you cross a task off, use its `"task"` value in the result message.

**Try it:** add a few tasks with different priorities, then ask what to do first. Your code never compares priorities. The bot reads the list and decides.

## Milestone 7: Keep It Safe
You already have one safety net: `MAX_TOOL_CALLS`, from milestone 3, stops a bot that keeps calling tools without ever answering you. Now add a second one.

**Unknown tools**. The bot might ask for a tool that doesn't exist. If `tool_name` isn't one of yours, don't crash. Save the result `"Unknown tool: "` followed by the name, so the bot can read it and try something else. That's one more `elif` for `complete_todo`, and an `else` for everything else.

Example output:

```
You: delete my first task
    [tool call] delete_todo {'number': 1}
Agent: I couldn't delete your first task because the delete tool isn't available right now.
```

**Try it:** add a line like `delete_todo, parameters: {"number": 1}` to the tool list in `TOOL_CALLS`, but don't write the function. Then ask the bot to delete a task and see what it does with the error. Agents can surprise you here. If you skip the extra line, the bot will just say it can't, since it only knows the tools you listed. Then set `MAX_TOOL_CALLS` to `1` and ask for two things in one message to trigger the limit.

## Milestone 8: Swap the Tools
Every new tool means another `elif` in your chain. A dictionary can replace the whole thing.

Here's the new trick: a function is a value, just like a number or a string, so it can be stored in a dictionary. Try this in a scratch file:

```python
def shout(text):
    return text.upper() + "!"

actions = {"shout": shout}
print(actions["shout"]("hello"))
```

Example output:

```
HELLO!
```

`actions["shout"]` looks up the function, and the parentheses at the end call it. Notice that `shout` has no parentheses inside the dictionary. You're storing the function, not running it.

Make a dictionary called `TODO_TOOLS` that maps each tool's name to its function and a short description of how to call it:

```python
TODO_TOOLS = {
    "add_todo": {
        "function": add_todo,
        "description": 'parameters: {"task": "...", "priority": "high" or "low"}. Call it once for each task the user lists.',
    },
    "list_todos": {
        "function": list_todos,
        "description": "parameters: {}",
    },
    "complete_todo": {
        "function": complete_todo,
        "description": 'parameters: {"number": 1}. Use list_todos first to check the task number.',
    },
}
```

Then change your program so that:

* Rename `PERSONALITY` to `TODO_PERSONALITY`. Everything about the to-do list now lives in one dictionary: `TODO_AGENT = {"name": "To-do list", "personality": TODO_PERSONALITY, "tools": TODO_TOOLS}`.

* Your chat loop moves out of `main` into a function, `run_agent(agent)`. It uses `tools = agent["tools"]` wherever it used to name a tool, so it shouldn't mention to-dos anywhere.

* One line, `result = tools[tool_name]["function"](tool_parameters)`, replaces the `if` and `elif` chain. Check `tool_name in tools` first, so unknown tools still work.
* The tool list in the prompt now comes from the dictionary too. Move the reply-format lines of your `TOOL_CALLS` into a constant called `FORMAT`, and delete the lines that list the tools. In run_agent, start from `FORMAT` and `"\nTools:"`, then add one line per tool in the form `name`, `description`, using a loop over `tools`. The system message is `agent["personality"]`, then `"\n"`, then that tool list. Rules that belong to one tool, like checking the list before completing a task, go in that tool's description.

In the dictionary, write `add_todo`, not `add_todo()`. With parentheses you'd call the function on the spot and store what it returns instead of the function.

Now write a second agent of your own: a name, a personality and a tools dictionary for something else, such as a finance tracker with add_expense (an amount and a category) and `get_total`. Put both agents in a dictionary, `AGENTS = {"1": TODO_AGENT, "2": FINANCE_AGENT}`. Then main prints each number and agent name, asks which one to talk to, and calls `run_agent` with that agent.

Example output:

```
Which agent do you want to talk to?
1. To-do list
2. Finance tracker
> 2
You: I spent 12.50 on lunch
    [tool call] add_expense {'amount': 12.5, 'category': 'lunch'}
Agent: Recorded 12.50 for lunch.
```

**Keep tools small.** The model can make mistakes, so only give it tools you'd be happy for it to get wrong. Never write a tool that runs any code the model sends (like `eval`), runs a command on your computer (like `os.system`), or deletes files. A tool that adds an expense is fine. A tool that can do anything is not.

**Try it:** look at what you changed to add the second agent. You wrote a personality and some tools, and you didn't touch the loop. Every agent you build from now on works this way!

### Troubleshooting
When something goes wrong with the model, your program stops with a `NotOpenAIError`. The last line of the error says what happened and starts with a code. Find the code here:


<table>
  <thead>
    <tr style="background-color: #f6f8fa; color: #333333; text-align: left;">
      <th style="padding: 8px 12px; border: 1px solid #dfe2e5;">Code</th>
      <th style="padding: 8px 12px; border: 1px solid #dfe2e5;">What it means</th>
      <th style="padding: 8px 12px; border: 1px solid #dfe2e5;">What to do</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>invalid_api_key</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Your key is missing or wrong.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Copy your key again from <a href="https://codeinplace.stanford.edu/cipx/build-an-agent/key">your key page</a>, and check that it's between the quotes in <code>ai.py</code>.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>key_disabled</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Your key has been turned off.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Fill out the <a href="https://codeinplace.stanford.edu/cipx/report">report form</a>.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>rate_limited</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">More than 30 requests in one minute.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Wait a minute, then run your program again.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>daily_limit_reached</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">You've used today's 500 requests.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Try again tomorrow. The count starts over at midnight UTC.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>quota_exhausted</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">You've used all 2,000,000 tokens.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Fill out the <a href="https://codeinplace.stanford.edu/cipx/report">report form</a>.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>input_too_large</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">The conversation is longer than 64,000 characters.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Restart your program, so the conversation starts fresh.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>invalid_request</code>,<br><code>unsupported_parameter</code>,<br><code>model_not_allowed</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Something in your call to <code>client.responses.create</code> isn't allowed, for example a model other than <code>"gpt-5-nano"</code>.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Read the rest of the message, which says what to change.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>upstream_error</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">The AI model had a hiccup.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Run your program again.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>incomplete</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">The model spent its whole answer thinking and sent back nothing.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Run it again, or ask for something shorter.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>network</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Your program couldn't reach the server, or it took too long to answer.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Check your internet connection and try again.</td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;"><code>certificate</code></td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Python couldn't check that it was talking to the real server.</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5; vertical-align: top;">Try a different network (school and work networks sometimes cause this), then fill out the <a href="https://codeinplace.stanford.edu/cipx/report">report form</a>.</td>
    </tr>
  </tbody>
</table>

Anything else? Post on the forum, but take your key out of any code you share.


