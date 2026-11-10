<h1>
  <a href="README.md"><img align="right" src="https://raw.githubusercontent.com/levg00/levg00/main/assets/lang-en-active-clean.svg" alt="EN"></a>
  <a href="README.ru.md"><img align="right" src="https://raw.githubusercontent.com/levg00/levg00/main/assets/lang-ru-inactive-clean.svg" alt="RU"></a>
  Deposit Manager
</h1>

[↩ Applied projects](https://github.com/levg00/levg00/blob/main/portfolio/applied.en.md)

A Python command-line application for tracking income and expenses. It lets users view transaction history, sort amounts, and export data to CSV.

Final course project for **CS50's Introduction to Programming with Python (CS50P)**.

### 📺 [`Project demo`](https://youtu.be/P-Ue0A0f01Q)


## 🛠️ Tools and implementation

* **Language:** Python 3 (no external dependencies)
* **Modules:** The standard `csv` module for working with data
* **Testing:** The `pytest` library for automated tests

### ⚡ Skills applied

* **File handling:** Implemented CSV history export with running balances and average income and expense amounts.
* **Collections and sorting:** Organized transaction storage, separation of income and expenses, and sorting by amount.
* **String processing:** Implemented user command parsing for adding transactions, viewing history, and exporting data.
* **Testing:** Wrote checks for balance changes, transaction history, and help text using `pytest`.

## Getting started

From the project directory:

```bash
python3 project.py
```

After starting the application, enter `help` to see the available commands. The application interface is in English.

## ⚙️ Main functions

<details>
<summary><b>📂 Function architecture</b></summary>

| Function | Purpose |
| :--- | :--- |
| `main()` | Runs the command loop: accepts input and calls the corresponding function. |
| `add_money(inp)` | Parses the income amount and description, increases the balance, and adds an entry to the history. |
| `withdraw_money(inp)` | Parses the expense amount and description, decreases the balance, and adds an entry to the history. |
| `print_history()` | Displays transactions in the order they were added, with the balance after each transaction. |
| `print_sorted()` | Separates income and expenses, sorts each group by amount in descending order, and displays them in two columns. |
| `export_csv()` | Writes the history and running balances to `history.csv`, adding the final balance and average transaction amounts. |
| `export_sorted_csv()` | Sorts the full history by amount in descending order and writes it to `sorted.csv`, adding the final balance and average transaction amounts. |
| `show_help()` | Returns the help text listing the available commands. |

The current state is stored in two global variables:

- `balance` — the current balance;
- `history` — a list of transactions in the format `(type, amount, description)`, where the type is `"+"` for income or `"-"` for an expense.

</details>

## 💾 Data export

`history.csv` contains the fields `Action`, `Amount`, `Description`, and `Balance`; `sorted.csv` contains `Action`, `Amount`, and `Description`. The final balance and average income and expense amounts are appended to each file.

> ⚠️ **Important:** Exporting again completely overwrites the file with the same name in the directory. To keep results from multiple sessions, rename the output files manually.


## 🧪 Project testing

You need `pytest` installed to run the tests. Run the following in your terminal:

```bash
python3 -m pip install pytest
python3 -m pytest -q test_project.py
```

The project includes **7 automated tests** checking the basic logic of adding income, recording expenses, and displaying help text.

> ⚠️ **Important:** Export tests create `history.csv` and `sorted.csv` in the working directory and may overwrite existing files.


## Usage example

```bash
$ python3 project.py
Deposit Manager
Type 'help' for commands
> add $500 salary
+$500.0 salary | Balance: $500.0
> withdraw $125 food
-$125.0 food | Balance: $375.0
> print history

HISTORY:
1. +$500.0 salary | Balance: $500.0
2. -$125.0 food | Balance: $375.0
> export csv
Exported: history.csv
> exit
```


> [!WARNING]
> **Limitations of the learning project:**
> * **Memory:** The history and balance are reset when the program exits.
> * **Precision:** Amounts use `float`, which can introduce floating-point representation errors.
> * **Validation:** Input validation is incomplete; invalid values are not rejected.


## Future improvements (Roadmap)

- [ ] Switch to `Decimal` for precise monetary amounts.
- [ ] Add validation and handle invalid commands without crashing the session.
- [ ] Implement saving and loading history between sessions (JSON/SQLite).
- [ ] Isolate the state of each test and verify output contents.


## Files

```text
project.py          — application
test_project.py     — original tests
examples/           — sample CSV files from the course project
README.md           — description and instructions in English
README.ru.md        — description and instructions in Russian
.gitignore          — excludes temporary files and generated output
```
