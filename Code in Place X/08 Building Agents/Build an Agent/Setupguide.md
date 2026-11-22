## What you're setting up
By the end of this guide you'll have Python and VS Code installed, and a program that runs on your own computer. It takes about 15 minutes, and the steps are the same on Windows and Mac except where marked.

You'll install:

* *Python 3.12* or newer, from python.org.
* *Visual Studio Code (VS Code)*, a free editor, with its Python extension.

You'll also see other options online, like Anaconda, uv or virtual environments. They're fine, but they add things you don't need for this assignment.

## Step 1: Install Python
Go to [python.org/downloads](https://www.python.org/downloads/) and click the big yellow download button. The site detects your operating system and gives you the right installer. Run it.

* *Windows:* on the first screen of the installer, tick **Add python.exe to PATH** before you click **Install Now**. This is the most common mistake in the whole setup. If you skip it, your computer won't know where Python is, and nothing later will work.
* *Mac:* click through the installer with the default options.

Now check that it worked. Open a terminal:

* **Windows:** press the Windows key, type **PowerShell**, and press Enter.
* **Mac:** press Cmd+Space, type **Terminal**, and press Enter.

Then run the command for your system:

<table>
  <thead>
    <tr style="background-color: #f6f8fa; color: #333333; text-align: left;">
      <th style="padding: 8px 12px; border: 1px solid #dfe2e5;">System</th>
      <th style="padding: 8px 12px; border: 1px solid #dfe2e5;">Command</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5;">Windows</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5;"><code>python --version</code></td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5;">Mac</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5;"><code>python3 --version</code></td>
    </tr>
  </tbody>
</table>


Example output:

```           
Python 3.12.7
```

Any version of 3.12 or higher is fine. If you get an error instead, jump to Troubleshooting at the bottom.

On a Mac the command is always `python3`, not `python`. On Windows it's `python`. Every command in this guide and the assignment gives both.

## Step 2: Install VS Code
Go to [code.visualstudio.com](https://code.visualstudio.com/) and download the installer for your system. Run it with the default options. On Windows, tick **Add to PATH** if the installer offers it.

Open VS Code, then add the Python extension:

1. Click the Extensions icon in the left sidebar (four squares), or press Ctrl+Shift+X (Cmd+Shift+X on a Mac).
2. Search for **Python**.
3. Install the one published by **Microsoft**. It has millions of downloads, so it's the first result.

The extension is what lets VS Code run your code, highlight errors, and find the Python you installed.

## Step 3: Open your project folder
For Build an Agent, your project folder is the starter code. Download it from the [assignment page](https://codeinplace.stanford.edu/cipx/build-an-agent) and unzip it somewhere you'll find it again, like your Desktop or Documents folder. (For any other project, make an empty folder with a name that has no spaces.)

1. In VS Code, choose **File → Open Folder** (on a Mac: **File → Open**).
2. Pick the unzipped folder itself, not the zip and not a folder inside it, and click **Open**. If VS Code asks whether you trust the authors, click **Yes**.
3. Create a file with the New File icon in the sidebar and name it `hello.py`.
4. Type `print("Hello, world")` in it and save with Ctrl+S (Cmd+S on a Mac).

Next, open VS Code's built-in terminal with **Terminal → New Terminal**. It opens at the bottom, already pointed at your project folder. Use this terminal for every command from here on.

## Step 4: Choose your Python
Your computer may have more than one Python on it. Tell VS Code to use the one you just installed:

1. Press Ctrl+Shift+P (Cmd+Shift+P on a Mac) to open the command palette.
2. Type **Python: Select Interpreter** and press Enter.
3. Choose the entry with the version you installed in Step 1 (3.12 or newer). On a Mac, pick one that says `/Library/Frameworks/...` or `/usr/local/bin/python3`, not `/usr/bin/python3`.

## Step 5: Run your program
Open hello.py and click the Run button (▷) in the top right of VS Code, or type the command for your system in the terminal:

<table>
  <thead>
    <tr style="background-color: #f6f8fa; color: #333333; text-align: left;">
      <th style="padding: 8px 12px; border: 1px solid #dfe2e5;">System</th>
      <th style="padding: 8px 12px; border: 1px solid #dfe2e5;">Command</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5;">Windows</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5;"><code>python hello.py</code></td>
    </tr>
    <tr>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5;">Mac</td>
      <td style="padding: 8px 12px; border: 1px solid #dfe2e5;"><code>python3 hello.py</code></td>
    </tr>
  </tbody>
</table>


Example output:

```
Hello, world
```

If you see that, your setup is done. You can delete `hello.py`.

## Troubleshooting
`python` is **not recognized (Windows)**. You probably skipped the PATH checkbox in Step 1. Run the Python installer again, choose **Modify**, then **Next**, and tick **Add Python to environment variables**. Then close and reopen VS Code.

`python` opens the **Microsoft Store (Windows)**. Same cause, same fix. You can also search for **Manage app execution aliases** in Settings and turn off the two Python entries.

**`python: command not found` (Mac)**. Use python3.

**The Run button uses an old Python.** Do Step 4 again and pick the version you installed.

**Nothing above helps.** Copy the full error message, including the command you ran, and post it in the forum.