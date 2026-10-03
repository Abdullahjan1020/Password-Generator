# 🔐 Password Manager (Python)

A desktop password manager built with Python and Tkinter. Generate strong random passwords, save them locally, and look them up later — all from a simple GUI.

## What it does

- Generates strong, random passwords (mix of letters, numbers, and symbols)
- Automatically copies the generated password to your clipboard
- Saves your website, email/username, and password locally
- Lets you search for a saved password by website name
- Warns you if you try to save an entry with missing fields

## How to use it

1. Enter the **website** and your **email/username**
2. Click **Generate Password** — a strong password is created and copied to your clipboard automatically
3. Click **Add** to save the entry
4. To find a saved password later, type the website name and click **Search**

## Files in this project

| File | What it does |
|------|---------------|
| `main.py` | Runs the app — handles the interface, password generation, saving, and searching |
| `logo.png` | Logo shown at the top of the window |
| `data.json` | Local file where your saved entries are stored (created automatically, not included in this repo) |

## How to run it

1. Make sure you have Python installed on your computer
2. Download or clone this repository
3. Install the one external library this project needs:

```bash
pip install pyperclip
```

4. Open a terminal in the project folder and run:

```bash
python main.py
```

Make sure `logo.png` stays in the same folder, since the app loads it by name.

## Requirements

- Python 3
- `tkinter` (comes built-in with Python; on some Linux systems you may need to install it separately)
- `pyperclip` (install with the command above)

## ⚠️ Note on security

This project stores passwords as plain text in a local `data.json` file, with no encryption. It was built for learning purposes — please don't use it to store real, sensitive passwords.

## About

This project was built as a way to practice GUI development with `tkinter`, working with local files (JSON), handling errors gracefully, and putting together a small but complete real-world tool.
