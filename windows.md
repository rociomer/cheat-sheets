### Useful tools for working in Windows

[Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/about)

The Windows Subsystem for Linux lets you run a GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup. Once installed, you can then choose your favorite GNU/Linux distribution from the Microsoft Store.

To install WSL 2, follow the instructions [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10).

To access WSL files from Powershell (replace ${YOUR_USERNAME} with your real username):
```
ls '\\wsl$\Ubuntu\home\${YOUR_USERNAME}'
```

---

[Visual Studio Code (VS Code)](https://code.visualstudio.com/)

VS Code is a source code editor which runs on your desktop and is available for Windows (as well as macOS and Linux). It has so many extensions which make it very powerful and highly customizable.

VS Code can be launched from within a WSL terminal by simply typing `code` into the WSL terminal from within the directory of your choice.
