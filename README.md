<h1>
  <a href="README.md"><img align="right" src="https://raw.githubusercontent.com/levg00/levg00/main/assets/lang-en-active-clean.svg" alt="EN"></a>
  <a href="README.ru.md"><img align="right" src="https://raw.githubusercontent.com/levg00/levg00/main/assets/lang-ru-inactive-clean.svg" alt="RU"></a>
  Deposit Manager
</h1>

[↩ Applied projects](https://github.com/levg00/levg00/blob/main/portfolio/applied.en.md)

A Python command-line application for tracking income and expenses. It lets you view transaction history, sort amounts, and export data to CSV.

Final course project for **CS50's Introduction to Programming with Python (CS50P)**.

[Video demonstration](https://youtu.be/P-Ue0A0f01Q)

## Tools and structure

**Python 3 · the standard `csv` module · pytest for testing.** No external libraries are needed to run the application.

The program is built around functions; command-line operations parse the input and call the functions for adding, withdrawing, viewing, and exporting. The balance and history are stored in memory for the current run.

The project combines:
- String processing
- Working with collections
- Sorting
- File input/output
- Testing

## Running the application

From the project folder:

```bash
python3 project.py
```

After starting the program, enter `help` to see the list of commands. The application interface is in English.

## Main functions

| Function | Purpose |
| :--- | :--- |
| `main()` | Starts the command loop: accepts input and calls the corresponding function. |
| `add_money(inp)` | Parses the income amount and description, increases the balance, and adds an entry to the history. |
| `withdraw_money(inp)` | Parses the expense amount and description, decreases the balance, and adds an entry to the history. |
| `print_history()` | Displays transactions in the order they were added, with the balance after each transaction. |
| `print_sorted()` | Separates income and expenses, sorts each group by amount in descending order, and displays them in two columns. |
| `export_csv()` | Writes the history and running balances to `history.csv`, adding the final balance and average transaction amounts. |
| `export_sorted_csv()` | Sorts the entire history by amount in descending order and writes it to `sorted.csv`, adding the final balance and average transaction amounts. |
| `show_help()` | Returns the help text with the available commands. |

The current state is stored in two global variables:
- `balance` — the current balance;
- `history` — a list of transactions in the format `(type, amount, description)`, where the type is `"+"` for income or `"-"` for an expense.

## Export

`history.csv` contains the fields `Action`, `Amount`, `Description`, and `Balance`; `sorted.csv` contains `Action`, `Amount`, and `Description`. The final balance and average income and expense transaction amounts are added at the end of each file.

**Exporting again overwrites the file with the same name.** To save multiple sessions, rename or copy the results.

## Tests

Existing tests:

```bash
python3 -m pip install pytest
python3 -m pytest -q test_project.py
```

The project includes seven tests. They check adding income, withdrawing expenses, and the help text. The other four tests call the display and export functions but do not yet check the contents of the results.

The export tests create `history.csv` and `sorted.csv` in the working folder and may overwrite existing files.

## Usage example

Enter the commands one at a time inside the program:

```text
add $500 salary
withdraw $125 food
print history
export csv
exit
```

After these transactions, the balance will be `$375.0`. The `export csv` command will create a `history.csv` file in the current working folder.

| Command | Action |
| :--- | :--- |
| `add $100 salary` or `+$100 salary` | Add income |
| `withdraw $50 food` or `-$50 food` | Add an expense |
| `print history` | Display transactions and running balances |
| `print sorted history` | Display income and expenses separately, by amount in descending order |
| `export csv` | Export the history to `history.csv` |
| `export sorted csv` | Export transactions by amount in descending order to `sorted.csv` |
| `help` | Display help |
| `exit` | Exit the program |

## Limitations of the course project version

- The history and balance are reset when the program exits. CSV files can be saved separately; importing them back is not implemented.
- Amounts use `float`, so fractional values may have representation errors.
- Input validation is incomplete: negative and special numeric values are not rejected. An unknown command terminates the program with an error.
- All input text, including transaction descriptions, is converted to lowercase.
- The `$` symbol is fixed in the interface; multiple currencies and transaction dates are not supported.

## Possible improvements

- Switch to `Decimal` for monetary amounts.
- Validate amounts and handle invalid commands without ending the session.
- Add saving and loading of the history between runs.
- Check the contents of the output and CSV files in tests, and isolate the state of each test.

## Files

```text
project.py          — application
test_project.py     — original tests
examples/           — sample CSV files from the course project
README.md           — description and instructions in Russian
.gitignore          — excludes temporary files and run outputs
```
