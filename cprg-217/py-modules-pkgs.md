### Modules and Packages

- In programming, a module is a piece of software that has a specific functionality.
- Modules in Python are just Python files with a .py extension. The name of the module is the same as the file name.
- A Python module can have a set of functions, classes, or variables defined and implemented.

---

### Advantages of Modularizing Code

- **Simplicity:** Rather than focusing on the entire problem at hand, a module typically focuses on one relatively small portion of the problem. If you’re working on a single module, you’ll have a smaller problem domain to wrap your head around. This makes development easier and less error-prone.

---

### Advantages of Modularizing Code

- **Maintainability:** Modules are typically designed so that they enforce logical boundaries between different problem domains. If modules are written in a way that minimizes interdependency, there is decreased likelihood that modifications to a single module will have an impact on other parts of the program.

---

### Advantages of Modularizing Code

- **Reusability:** Functionality defined in a single module can be easily reused (through an appropriately defined interface) by other parts of the application. This eliminates the need to duplicate code.

---

### Advantages of Modularizing Code

- **Scoping:** Modules typically define a separate [**namespace**](https://realpython.com/python-namespaces-scope/), which helps avoid collisions between identifiers in different areas of a program. (One of the tenets in the [Zen of Python](https://realpython.com/zen-of-python/) is *Namespaces are one honking great idea—let’s do more of those!*)

---

### Define a Module in Python

1. A module can be written in Python itself.
2. A module can be written in **C** and loaded dynamically at run-time, like the `re` ([**regular expression**](https://realpython.com/regex-python/)) module.
3. A **built-in** module is intrinsically contained in the interpreter, like the [`itertools` module](https://realpython.com/python-itertools/).

---

### Create a Module

- Create a file that contains legitimate Python code and then give the file a name with a `.py` extension. That’s it! No special syntax is necessary.

```python
# mod.py
# defined objects: string s, list a, function foo, class Foo
s = "If Comrade Napoleon says it, it must be right."
a = [100, 200, 300]

def foo(arg):
    print(f'arg = {arg}')

class Foo:
    pass
```

---

### Import a Module

- Assuming `mod.py` is in an appropriate location, objects defined in module `mod` can be accessed by **importing** the module.

```python
import mod

print(mod.__file__)
print(mod.s)
print(mod.a)
mod.foo(["quux", "corge", "grault"])
x = mod.Foo()
print(x)
```

---

### The Module Search Path

- The directory from which the input script was run or the **current directory** if the interpreter is being run interactively.
- The list of directories contained in the [`PYTHONPATH`](https://docs.python.org/3/using/cmdline.html#envvar-PYTHONPATH) environment variable, if it is set.
- An installation-dependent list of directories configured at the time Python is installed

---

### The Module Search Path

- The resulting search path is accessible in the Python variable `sys.path`, which is obtained from a module named `sys`:

```python
import sys
print('\n'.join(sys.path))

# /home/student/extra-mod-pkg
# /usr/lib/python313.zip
# /usr/lib/python3.13
# /usr/lib/python3.13/lib-dynload
# /home/student/extra-mod-pkg/.venv/lib/python3.13/site-packages
```

---

### The `import` Statement

- **Module** contents are made available to the caller with the `import` statement. The `import` statement takes many different forms.
- Each module has its own **private symbol table**. A module creates a separate **namespace**.
- From the caller, objects in the module are only accessible when prefixed with `<module_name>` via **dot notation**.

---

### The `import` Statement

```python
import mod

print(mod)
# <module 'mod' from '/home/student/extra-mod-pkg/mod.py'>

s # NameError: name 's' is not defined
foo("quux") # NameError: name 'foo' is not defined

print(mod.s)
mod.foo("quux")
```

---

### Alternate Form of the `import` Statement

- `from <module_name> import <name(s)>` allows individual objects from the module to be imported *directly into the caller’s symbol table*.
- Warning: any objects that already exist with the same name will be *overwritten*.

```python
a = ['foo', 'bar', 'baz']
print(a)

from mod import s, foo, a
print(s)
foo('quux')
print(a)
```

---

### Alternate Form of the `import` Statement

- It is even possible to indiscriminately `import` everything from a module:

  `from <module_name> import *`

- This isn’t recommended in large-scale production code. Unless you know them all well and can be confident there won’t be a conflict, you have a decent chance of overwriting an existing name inadvertently.

---

### Alternate Form of the `import` Statement

- It is also possible to `import` individual objects but enter them into the local symbol table with alternate names.

```python
from mod import s as string, a as alist

s = "foo"
print(s)
a = ["foo", "bar", "baz"]
print(a)
print(string)
print(alist)
```

---

### Alternate Form of the `import` Statement

- You can also import an entire module under an alternate name.

  `import <module_name> as <alt_name>`

```python
import mod as my_module

print(my_module.a)
print(my_module.s)
my_module.foo("quux")
```

---

### The `dir()` Function

- The built-in function `dir()` returns a list of defined names in a namespace. Without arguments, it produces an alphabetically sorted list of names in the current **local symbol table**.

```python
import mod

print(dir())
# ['__annotations__', '__builtins__', '__cached__',
# '__doc__', '__file__', '__loader__', '__name__',
# '__package__', '__spec__', 'mod']
print(dir(mod))
# ['Foo', '__builtins__', '__cached__', '__doc__',
# '__file__', '__loader__', '__name__', '__package__',
# '__spec__', 'a', 'foo', 's']
```

---

### Executing a Module as a Script

- Any `.py` file that contains a **module** is essentially also a Python **script**, and there isn’t any reason it can’t be executed like one.

```python
# mod2.py
s = "If Comrade Napoleon says it, it must be right."
a = [100, 200, 300]

def foo(arg):
    print(f'arg = {arg}')

class Foo:
    pass

print(s)
print(a)
foo('quux')
print(Foo())
```

---

### Executing a Module as a Script

- Execute the `mod2.py`, and it works just like a regular Python script.

  ```shell
  python mod2.py
  If Comrade Napoleon says it, it must be right.
  [100, 200, 300]
  arg = quux
  <__main__.Foo object at 0x7a99c7136e40>
  ```

---

### Executing a Module as a Script

- Unfortunately, now it also generates output when imported as a module.

```python
import mod
```

```shell
If Comrade Napoleon says it, it must be right.
[100, 200, 300]
arg = quux
<mod.Foo object at 0x0169AD50>
```

---

### Executing a Module as a Script

- When a `.py` file is imported as a module, Python sets the special **dunder** variable [`__name__`](https://realpython.com/python-main-function/) to the name of the module.
- However, if a file is run as a standalone script, `__name__` is (creatively) set to the string `'__main__'`. Using this fact, you can discern which is the case at run-time and alter behavior accordingly.

---

### Executing a Module as a Script

```python
s = "If Comrade Napoleon says it, it must be right."
a = [100, 200, 300]

def foo(arg):
    print(f'arg = {arg}')

class Foo:
    pass

if (__name__ == '__main__'):
    print(s)
    print(a)
    foo('quux')
    print(Foo())
```

---

### Python Packages

- As the number of modules grows, it becomes difficult to keep track of them all if they are dumped into one location. This is particularly so if they have similar names or functionality.
- **Packages** allow for a hierarchical structuring of the module namespace using **dot notation**.
- In the same way that **modules** help avoid collisions between global variable names, **packages** help avoid collisions between module names.

---

### Python Packages

- Creating a **package** is quite straightforward, since it makes use of the operating system’s inherent hierarchical file structure.
- There is a directory named `pkg` that contains two modules, `mod1.py` and `mod2.py`.

```shell
pkg
├── mod1.py
└── mod2.py
```

---

### Python Packages

```python
# pkg/mod1.py
def foo():
    print('[mod1] foo()')

class Foo:
    pass
```

```python
# pkg/mod2.py
def bar():
    print('[mod2] bar()')

class Bar:
    pass
```

---

### Import Modules in Packages

- If the `pkg` directory resides in a location where it can be found (in one of the directories contained in `sys.path`), you can refer to the two **modules** with **dot notation** (`pkg.mod1`, `pkg.mod2`) and import them.

```python
import pkg.mod1, pkg.mod2

pkg.mod1.foo()
pkg.mod2.bar()
```

---

### Package Initialization

- If a file named `__init__.py` is present in a package directory, it is invoked when the package or a module in the package is imported.
- This can be used for execution of package initialization code, such as initialization of package-level data.

```shell
pkg
├── __init__.py
├── mod1.py
└── mod2.py
```

---

### Package Initialization

- Print a message and define a list `A` in `__init__.py`

```python
# __init__.py
print(f'Invoking __init__.py for {__name__}')
A = ['quux', 'corge', 'grault']
```

- When the package is imported, the global list `A` is initialized

```python
import pkg
# Invoking __init__.py for pkg
print(pkg.A)
# ['quux', 'corge', 'grault']
```

---

### Package Initialization

- A **module** in the package can access the global variable by importing it in turn.

```python
# pkg/mod1.py
def foo():
    from pkg import A
    print('[mod1] foo() / A = ', A)

class Foo:
    pass
```

---

### Package Initialization

- `__init__.py` can also be used to effect automatic importing of modules from a package.

```python
# __init__.py
print(f'Invoking __init__.py for {__name__}')
import pkg.mod1, pkg.mod2
```

- When you execute `import pkg`, modules `mod1` and `mod2` are imported automatically.

```python
import pkg
pkg.mod1.foo()
pkg.mod2.bar()
```

---

### Key Takeaways

- Modularizing code improves simplicity, maintainability, reusability, and namespace scoping, reducing errors and code duplication.
- Python modules are individual `.py` files that group related functions, classes, and variables, making code easier to organize and reuse.
- Various forms of the `import` statement.
- The Python module search path: `sys.path`.

---

### Key Takeaways

- Packages are directories containing multiple modules (and optionally an `__init__.py` file), enabling hierarchical module organization and avoiding naming conflicts.
- The `__init__.py` file in a package can initialize package-level data and control module imports when the package is imported.

---

### Sources:

- https://realpython.com/python-modules-packages/
- https://docs.python.org/3/reference/import.html
- https://docs.python.org/3/tutorial/modules.html