# Common Juju Errors and How to Fix Them
When using juju via CLI,following errrors can occur .

# 1. `Juju Bootstrap` Error: Cloud Not Found

This error usually appears when you try to bootstrap a controller without specifying a valid cloud name.

# How to Fix:

Use a valid cloud name from the list of available clouds. To see available clouds, run:

```bash
juju clouds
```

Then use one of those clouds in your bootstrap command:

```bash
juju bootstrap lxd my-controller
```

# Permission denied or access denied on Windows

This error occurs when you may not have admin rights or execution permission to install or run Juju.To fix this error ,define a clear path for your system .In case of error,your terminal will show error like

!!! error "Command Not Recognized"
    ```bash
    'juju' is not recognized as an internal or external command,
    operable program or batch file.
    ```


This error means that your computer doesn’t know where to find the Juju program. The system looks for executable programs in the "PATH" environment variable, and Juju hasn’t been added to that list yet.



# How to fix


??? info "Steps to Add Juju to PATH on Windows"
    ```
    Find the location where juju.exe is saved

    Add this folder to your system PATH:

    1. Open Start Menu and search for "Environment Variables"
    2. Click "Edit the system environment variables"
    3. In the System Properties window, click "Environment Variables..."
    4. Under System variables, select "Path"
    5. Click "New", then paste the Juju path (e.g., C:\Program Files\juju)
    6. Click OK to save and exit all dialogs
    ```

Then, Restart your terminal and Run the command again

```bash
juju version
```

You should now see something like


```
3.4.0-ubuntu-amd64
```


 !!! tip "Pro Tip"
    If you still see the error after updating PATH, restart your computer to make sure the environment variable changes take effect.