# 📌 README: Creating and Using an Alias Script in Linux

This guide explains how to create a script that defines an alias, how to
activate it correctly, and how to bypass the alias when needed.

------------------------------------------------------------------------

# 🚀 1. What the Script Does

You need a script named **`0-alias`** that creates an alias:

-   **Alias Name:** `ls`\
-   **Alias Value:** `rm *`\
    (This replaces the normal `ls` command with a delete command.)

### Script content:

``` bash
#!/bin/bash
alias ls='rm *'
```

⚠️ **Warning:**\
This alias makes `ls` dangerous because it deletes all files in the
current directory.\
Use only in a safe/test folder like **/tmp**.

------------------------------------------------------------------------

# 🚀 2. Why "source" Must Be Used

Simply running the script like this:

``` bash
./0-alias
```

will **not** set the alias in your current shell.\
That's because this command launches a new temporary shell and closes it
after execution.

To activate the alias in your current shell, use:

``` bash
source ./0-alias
```

or

``` bash
. ./0-alias
```

### What `source` does:

-   Runs the script **inside your current terminal session**
-   Applies any aliases or variables immediately
-   Keeps them active until you close the terminal

------------------------------------------------------------------------

# 🚀 3. What Happens After Sourcing

Once you run:

``` bash
source ./0-alias
```

Then:

``` bash
ls
```

will actually run:

``` bash
rm *
```

This deletes all files in the current directory.

------------------------------------------------------------------------

# 🚀 4. How to Bypass the Alias (`\ls`)

To use the real `ls` command instead of the alias, type:

``` bash
\ls
```

### Why this works:

-   The backslash (`\`) tells the shell:\
    **"Ignore all aliases and run the original command."**

------------------------------------------------------------------------

# 🚀 5. Useful Alias Management Commands

### ✔ Show all aliases:

``` bash
alias
```

### ✔ Remove an alias:

``` bash
unalias ls
```

### ✔ Temporarily disable alias in one command:

``` bash
\command
```

------------------------------------------------------------------------

# 🧠 Summary

  Feature                         Explanation
  ------------------------------- -------------------------------------
  Script defines alias            `alias ls='rm *'`
  Why use `source`                Loads alias into your current shell
  What `ls` does after sourcing   Deletes files (`rm *`)
  What `\ls` does                 Bypasses alias and shows real `ls`
  How to remove alias             `unalias ls`