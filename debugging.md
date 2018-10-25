# Debugging

```Shell
$ python -m pdb my_script.py
```

This causes the debugger to stop the execution on the first statement.

Or we can set break points in the script itself.

```Python
import pdb

def foo():
    pdb.set_trace()
    return "Chubby Bunny"

print(foo())
```

Try to run this script we will enter the debugger.

At pdb prompt, `help` to list all the commands, `help <command>` to display
the information about this `<command>`. A few useful commands:

- `c`: continue execution
- `w`: show the context
- `a`: print the argument list
- `s`: step
- `n`: next
