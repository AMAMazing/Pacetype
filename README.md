# Pacetype 🐢

[![PyPI version](https://badge.fury.io/py/pacetype.svg)](https://badge.fury.io/py/pacetype)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Simulates typing text and emojis character-by-character with adjustable delays. Uses the clipboard for robust cross-platform compatibility, especially for special characters and emojis that often cause issues with direct key simulation.

## 🤔 Why Pacetype?

Automating keyboard input with libraries like `pyautogui` can be tricky when dealing with emojis or complex Unicode characters. Direct key simulation doesn't always map correctly across different OSs and input methods.

`pacetype` simplifies this by:

1.  Copying one character (including emojis) at a time to the system clipboard.
2.  Simulating the standard "paste" keyboard shortcut (Ctrl+V or Cmd+V).
3.  Waiting for a specified interval (if provided) before the next character.

This clipboard-based method ensures greater reliability for a wide range of characters.

## 🚀 Installation

```bash
pip install pacetype
```

## ✨ Simple Usage

Using pacetype is straightforward. Just import it and call it directly with the text you want to type.

```python
import pacetype
import time

# Give yourself a moment to switch to the target window
print("Pacetyping in 3 seconds...")
time.sleep(3)

# Type text with the default delay (~0.1 seconds between characters)
pacetype("Hello World! 👋")

# Type text with a custom delay (0.5 seconds between characters)
pacetype("Typing slowly... 🐢", interval=0.5)

# Pacetype inherently has a small delay due to the copy/paste mechanism,
# even if interval is 0.0.
pacetype("Fast typing!", interval=0.0)

print("Typing finished!")
```

### Key Points:

*   **Default Delay:** By default, pacetype uses a `0.05` second delay between characters (`pacetype("text")` is equivalent to `pacetype("text", interval=0.05)`). This is defined in `pacetype/__init__.py`.
*   **Inherent Delay:** Even if you set `interval=0.0`, there will always be a small, system-dependent delay between characters due to the time it takes to perform the clipboard copy and paste operations. There is no artificial `time.sleep(0.01)` added when the interval is 0.

## ⚙️ Features

*   **Emoji & Unicode Support:** Reliably types emojis and complex characters via the clipboard.
*   **Adjustable Delay:** Control typing speed with the optional `interval` argument.
*   **Simple Callable API:** Just `import pacetype` and use `pacetype("your text", interval=...)`.
*   **Cross-Platform:** Works on Windows, macOS, and Linux (thanks to `pyperclip` and `pyautogui`).

## ⚠️ Important Notes

*   **Window Focus:** The target application window (e.g., text editor, browser, chat) must have keyboard focus when `pacetype()` is executing.
*   **Clipboard Use:** Pacetype relies heavily on the system clipboard. Any content you manually copy while it's running will be overwritten. The clipboard will contain the last character typed after the script finishes.
*   **Keyboard Shortcuts:** Assumes standard `Ctrl+V` (Windows/Linux) or `Cmd+V` (macOS) paste shortcuts are active.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
