### What is Win32 API?

- **Win32** is an application programming interface (API) developed by Microsoft. It is dedicated to 32-bit Windows operating systems.
- Using this API, developers benefit from a set of functions for creating Windows applications using programming languages such as C, [C++](https://datascientest.com/en/c-what-is-this-computer-language-for) and Visual Basic.

[Programming reference for the Win32 API](https://learn.microsoft.com/en-us/windows/win32/api/)

---

### What is pywin32?

- **PyWin32** is a Python library that lets you access the low-level features of the Windows operating system, its specific functions and its APIs via bindings.
- The aim of **PyWin32**  is to provide bindings for Win32 APIs, enabling developers to create Python scripts that can control and manipulate Windows elements. This includes processes, threads, windows, files, registries and services.

---

### pywin32's Main Applications

- Create graphical user interfaces using libraries such as the **Win32 API and MFC.**
- Manipulate Windows text and binary files, as well as Office software files such as Word, Excel and PowerPoint. These files can be created, modified or saved using Python scripts.
- Automate system tasks. Examples include data backup, task scheduling, Windows service control and user account management.

---

### Win32 API Example - Beep function

- Generates simple tones on the speaker. The function is synchronous; it performs an alertable wait and does not return control to its caller until the sound finishes.
- `dwFreq`: The frequency of the sound, in hertz.
- `dwDuration`: The duration of the sound, in milliseconds.

```c++
BOOL Beep(
  [in] DWORD dwFreq,
  [in] DWORD dwDuration
);
```

[win32api.Beep](https://mhammond.github.io/pywin32/win32api__Beep_meth.html)

---

### pywin32 Example - Beep

```python
import win32api

def main():
    # Frequency (in Hertz) and duration (in milliseconds)
    frequency = 1000  # 1000 Hz
    duration = 500  # 0.5 second
    # Call Beep
    win32api.Beep(frequency, duration)

if __name__ == "__main__":
    main()
```

---

### Win32 API Example - FindFiles function

- Retrieves a list of matching filenames. An interface to the API FindFirstFile/FindNextFile/Find close functions.
- `fileSpec`: A string that specifies a valid directory or path and filename, which can contain wildcard characters (`*` and `?`).

[win32api.FindFiles](https://mhammond.github.io/pywin32/win32api__FindFiles_meth.html)

---

### pywin32 Example - FindFiles

```python
import win32api

# Find files with .py extension in the current directory
files = win32api.FindFiles('*.py')

for file_info in files:
    # file_info is a tuple with details about the file
    # file_info[8] is the file name
    print(file_info[8])
```

---

### Win32 API Example - win32net.NetServerGetInfo

- `dict = NetServerGetInfo(server, level)`
- Retrieves information about a particular server.
- `server`: The name of the server to execute on.
- `level`: The information level contained in the data.

---

### pywin32 Example - win32net.NetServerGetInfo

```python
import win32net

# Get information about the local computer (server)
server_name = None  # None means local computer
level = 101  # Level of detail (101 is common for general info)

server_info = win32net.NetServerGetInfo(server_name, level)

# Print server name and platform ID
print("Server Name:", server_info["name"])
print("Platform ID:", server_info["platform_id"])
print("Version:", server_info["version_major"], ".", server_info["version_minor"])
print("Server Type:", server_info["type"])
```

---

### Key Takeaways

- **pywin32** is a powerful bridge between Python and the Windows operating system.
- It enables Python developers to leverage the full capabilities of Windows APIs and automate complex workflows that are otherwise accessible only through native code.

---

### Sources:

- https://github.com/mhammond/pywin32
- https://mhammond.github.io/pywin32/
- https://mhammond.github.io/pywin32/modules.html
- https://datascientest.com/en/pywin32-unveiling-the-python-extension-exclusively-for-windows-systems
