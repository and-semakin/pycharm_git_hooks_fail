# PyCharm loses commit info if git hook fails

PyCharm (and probably another IDEA-based IDEs as well)
doesn't preserve Git commit info, such as:
* commit message;
* selected files/lines;

if Git hooks fails and interrupts commit process.

## Setup

1. Clone this repo;

2. Create always failing Git hook:

    ```shell script
    cat <<EOT >> .git/hooks/pre-commit
    echo "Fail!"
    false
    EOT
    chmod +x .git/hooks/pre-commit
    ```

3. Try changing two different files: `1.txt` and `2.txt`;

4. Open "Commit Changes" window (Ctrl+K or Cmd+K);

5. Type some commit message, add one file to commit but don't add another;

6. "Run Git hooks" option should be enabled;

7. Commit it, it will fail;

8. Open "Commit Changes" window again;

9. Where is your changes (message, selected files)? Everything was reset to default values.
