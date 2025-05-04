### What is a scripting language?

- A **scripting language** is a type of programming language that is interpreted rather than compiled. It is typically used to **automate tasks**, **control software applications**, or **glue together components** of a system.
- Scripts are often written to be executed by an **interpreter**, which reads and executes the code line-by-line at runtime, rather than being compiled into machine code beforehand.

---

### Key Characteristics of Scripting Languages

- **Interpreted, not compiled**

  Scripting languages are usually interpreted, meaning the code is executed directly without a separate compilation step.

- **High-level and easy to use**

  They are designed to be simple and expressive, allowing developers to write code quickly and with fewer lines.

---

### Key Characteristics of Scripting Languages

- **Automation-focused**

  Scripting languages are often used to automate repetitive tasks, such as file manipulation, system administration, or web scraping.

- **Integration with other systems**

  They are commonly used to integrate and communicate with other programs, APIs, or system components.
---

### Key Characteristics of Scripting Languages

- **Rapid development and prototyping**

  Scripting languages support fast development cycles, making them ideal for prototyping and small-scale applications.

---

### Examples of Scripting Languages

- **Python**: Web development, automation, data science
- **JavaScript**: Web development (client and server-side)
- **Bash**: Shell scripting, system administration, DevOps tasks
- **Powershell**: Windows automation, DevOps tasks

---

### Examples of Scripting Languages

- **Ruby**: Web development, scripting, automation
- **PHP**: Server-side web development
- **Perl**: Text processing, system administration

---

### Scripting Languages vs. Programming Languages

![script.vs.prog-1](./unit-01-slides.assets/script-prog-1.webp)

---

### Scripting Languages vs. Programming Languages

![script.vs.prog-2](./unit-01-slides.assets/script-prog-2.webp)

---

### Scripting Languages vs. Programming Languages

- The line between scripting and programming languages is becoming increasingly blurred.

- Many modern languages like Python and JavaScript can be used for both scripting and full-scale application development.

---

### You can compile Python

- Whenever you run a Python program, that program (and anything it imports) will be compiled from Python source code to Python bytecode, and then the bytecode is what’s executed.
- This all happens automatically for you, and you might not even notice it happening. 
- You can run an explicit compilation step on a Python application, to compile the source code to bytecode. It’s just relatively rare to do so.

---

### Real-world uses for scripting language

- Real-life systems are made up of multiple programs all working together. Scripts can be used to help each separate program work together.
- Different scripting languages have different capabilities. For example, you might use PHP to manage cookies and manipulate databases. Or you might use Ruby to write code for web applications designed to run on specific operating systems.

---

### Big names that use scripting languages

- Node.js is used in the real world for the apps of big-name companies like Paypal, Netflix, eBay, Uber, and LinkedIn.

- PHP is popular for use by global websites, including Etsy, WordPress, Facebook, Slack, and Wikipedia.

---

### Big names that use scripting languages

- Ruby is commonly used on applications like Hulu, MyFitnessPal, Goodreads, and Airbnb.

- Python is a general-purpose programming language used by well-known companies such as Netflix, Google, and Goldman Sachs.

---

### Required skills

- Curiosity
- The desire to solve problems
- Excellent communication
- The ability to work as part of a team
- Patience and positivity
- Accountability

---

### What is Python?


- Python is a **high-level**, **interpreted**, and **general-purpose** programming language.
- Created by Guido van Rossum and first released in 1991.
- Known for its **simple syntax**, **readability**, and **versatility**.
---

### Why Use Python as a Scripting Language?

- **Cross-Platform Compatibility**:
  - Runs on Windows, macOS, Linux, and more.
  - Write once, run anywhere (with minimal changes).
- **Easy to Learn and Read**
  - Clean and minimal syntax.
  - Great for beginners and rapid development.
  - Uses indentation to define code blocks.

---

### Why Use Python as a Scripting Language?

- **Very Extensive Standard Library**
  - Comes with "batteries included".
  - Built-in modules for:
    - File I/O
    - Networking
    - System administration
    - Data parsing (JSON, XML, CSV)

---

### Why Use Python as a Scripting Language?

- **Extensive Third-Party Libraries via PyPI**
  - Libraries for:
    - Web development (Flask, Django, FastAPI)
    - Automation (Requests, Playwright)
    - DevOps (Ansible, Fabric)
    - Data science (Pandas, NumPy)

---

### Why Use Python as a Scripting Language?

- **Great for Automation**
  - Ideal for writing scripts to automate:
    - File and directory operations
    - Text processing
    - System monitoring
    - Web scraping

---

### Why Use Python as a Scripting Language?

- **Active Community and Support**

  - Large, active community.

  - Abundant tutorials, forums, and documentation.

  - Great for troubleshooting and learning.

---

### Python is the Lingua Franca of ML/AI

- Python gets rid of as much of the ML/AI developmental complexity as possible.
- Python is the dominant language in the AI/ML field. Most research, development, and job opportunities in AI heavily involve Python.
- Rich Ecosystem of AI/ML Libraries: TensorFlow, PyTorch, Keras, Scikit-learn, Pandas, NumPy.

---

### Python vs. Other Scripting Languages

![py-other-scripting](./unit-01-slides.assets/py-other-scripting.webp)

---

### Set Up Python Development Environment

- *Environment setup* is the process of organizing your computer so you can write code. This involves:
  - Installing any necessary tools
  - Configuring them
  - Handling any hiccups during the setup
- There is no single setup process because everyone has a different computer with a different operating system, version of the operating system, and version of the Python interpreter.

---

### Set Up Python Development Environment

1. [How to Install Python on Your System: A Guide](https://realpython.com/installing-python/)
2. [Set Up Your Python Development Environment](https://learn.microsoft.com/en-us/windows/python/beginners#manually-set-up-your-python-development-environment)
3. [Python Virtual Environments](https://realpython.com/python-virtual-environments-a-primer/)
4. [uv - Python package and project manager](https://docs.astral.sh/uv/)

---

### Your First Python Script

```python
# This is a simple Python script that demonstrates the basic print function
# by outputting "Hello World!" to the console/terminal.

# How to run this script:
# 1. Open a terminal/command prompt
# 2. Navigate to the directory containing this file using: cd path/to/directory
# 3. Run the script using one of these commands:
#    - On Windows: python hello.py
#    - On Linux/Mac: python3 hello.py

# The print() function below displays text to the console
# The text "Hello World!" is passed as a string argument (enclosed in quotes)
print("Hello World!")
```

[How to Run Your Python Scripts and Code](https://realpython.com/run-python-scripts/)

---

### Command-Line Interfaces in Python

- **Online tutorials:**

  - [Argparse Tutorial](https://docs.python.org/3/howto/argparse.html)

  - [Build Command-Line Interfaces With Python's argparse](https://realpython.com/command-line-interfaces-python-argparse/)

  - [Master Python's argparse Module: Build Better CLIs](https://www.datacamp.com/tutorial/python-argparse)

---

### Working With Files in Python

- **Online tutorials:**
  - [Reading and Writing Files in Python (Guide)](https://realpython.com/read-write-files-python/)
  - [Working with files in Python](https://realpython.com/working-with-files-in-python/)
  - [Reading binary files in Python](https://www.pythonmorsels.com/reading-binary-files-in-python/)
  - [Python's pathlib Module: Taming the File System](https://realpython.com/python-pathlib/)

---

### Hashing Algorithms in Python

- **Online tutorials:**
  - [What Is Hashing, and How Does It Work?](https://www.codecademy.com/resources/blog/what-is-hashing/)
  - [`hashlib` — Secure hashes and message digests](https://docs.python.org/3/library/hashlib.html)
  - [How to Use Hashing Algorithms in Python using hashlib](https://thepythoncode.com/article/hashing-functions-in-python-using-hashlib)

---

### Run Shell Commands From Python

- **Online tutorials:**
  - [An Introduction to Python Subprocess](https://www.datacamp.com/tutorial/python-subprocess)
  - [The Right Way to Run Shell Commands From Python](https://martinheinz.dev/blog/98)
  - [`sh` module](https://github.com/amoffat/sh)

---

#### Sources:

- https://www.coursera.org/ca/articles/scripting-language
- https://algodaily.com/lessons/scripting-vs-programming/differences-between-scripting-languages-and-programming-languages
- https://www.b-list.org/weblog/2023/dec/06/compile-python-bytecode/
