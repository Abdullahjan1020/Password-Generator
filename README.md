# Password Manager

A small desktop password manager built with Python and Tkinter. The application generates strong random passwords, copies generated passwords to the clipboard, confirms saved details through a dialog box, and stores records in a local text file.

## How the project is built

The program is a single-file desktop application:

- `main.py` creates the Tkinter window and contains the password generator and save workflow.
- `logo.png` is loaded by the Tkinter `PhotoImage` widget and displayed at the top of the window.
- `data.txt` is the local append-only storage file for saved website, email/username, and password records.

Run the program from this folder with:

```bash
python main.py
```

The working directory should contain `logo.png`, because the application loads that image using its relative filename.

## Modules used

- `tkinter` and `tkinter.messagebox` provide the graphical interface, input fields, buttons, and confirmation dialogs.
- `random.choice`, `random.randint`, and `random.shuffle` create and mix password characters.
- `pyperclip` copies generated passwords to the system clipboard.

Install the external dependency with:

```bash
pip install pyperclip
```

Tkinter is included with most standard Python installations. On some Linux distributions it may need to be installed separately through the operating system package manager.

## Main functionality

1. Enter a website and email or username.
2. Click **Generate Password** to create a password containing lowercase letters, numbers, and symbols.
3. The generated password is inserted into the password field and copied automatically to the clipboard for convenient pasting.
4. Click **Add** to validate the form. The website, email/username, and password fields are all required.
5. Review the entered website, email, and password in a confirmation dialog box.
6. Confirm the dialog to append the record to `data.txt`.
7. The website and password fields are cleared after a successful save, while the email field remains available for the next entry.

### Empty-field validation

When **Add** is clicked, the program checks whether any of the three input fields is empty. If the website, email/username, or password field has no value, the record is not saved. Instead, an **Oops** dialog asks the user to fill in every field. The confirmation dialog is shown only after all fields contain values.

## Dialog box experience

The application uses dialogs at the important points in the workflow:

- An **Oops** information dialog appears when any required input field is empty and asks the user to fill in the missing fields.
- A confirmation dialog displays the website, email, and password before saving, allowing the user to cancel or approve the operation.

This gives the user a clear chance to catch incorrect details before they are written to the local file.

## Clipboard behavior

After password generation, `pyperclip.copy()` places the generated password on the system clipboard. This means the password can be pasted immediately into another application without selecting and copying it manually.

## Storage and security note

Records are stored as plain text in `data.txt`. This project is intended for practice and local learning. Do not use it for real credentials without adding encryption, secure access controls, and safer credential storage. Avoid committing real passwords or other sensitive data to a public repository.

## Current version

The current version of the application has been upgraded from the original
append-only text-file workflow described above. The original documentation is
kept unchanged as a record of the project's history.

### New features and changes

- Uses the `json` module to store password records in a structured format.
- Saves records to a local `data.json` file instead of appending to `data.txt`.
- Updates existing JSON data when a new website record is saved.
- Creates `data.json` automatically when the file does not yet exist.
- Adds a **Search** button for finding saved credentials by website.
- Displays the saved email/username and password in a message box when a
  website is found.
- Displays an error message when no local data file exists or when no record
  matches the requested website.
- Adds `try`/`except FileNotFoundError` handling when saving and searching, so
  the application does not crash when `data.json` is missing.
- Uses `else` and `finally` blocks in the save workflow to update existing
  records and clear the website and password fields after the operation.
- Removes the save confirmation dialog; valid entries are saved immediately.
- Keeps required-field validation for the website, email/username, and
  password fields.
- Restores the default email address in the email/username field.
- Changes the website field layout to a narrower field beside the Search
  button.

### Local data file

When the program runs and a password is saved, it creates `data.json` on the
local machine if it does not already exist. The file contains the website,
email/username, and password credentials entered by the user, and is used by
the Search feature.

For privacy and security, `data.json` is excluded from version control through
`.gitignore`. It must not be committed to this public repository because it
contains local credentials. The application should be used for learning only;
real credentials should be protected with encryption and safer credential
storage.
