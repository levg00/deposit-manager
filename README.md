<h1>
  <a href="README.md"><img align="right" src="https://raw.githubusercontent.com/levg00/levg00/main/assets/lang-en-active-clean.svg" alt="EN"></a>
  <a href="README.ru.md"><img align="right" src="https://raw.githubusercontent.com/levg00/levg00/main/assets/lang-ru-inactive-clean.svg" alt="RU"></a>
  Deposit Manager
</h1>

[↩ Applied projects](https://github.com) 



A Python command-line application for tracking income and expenses. It lets you view transaction history, sort amounts, and export data to CSV.

Final course project for **CS50's Introduction to Programming with Python (CS50P)**.



### 📺 [`Video demonstration`](https://youtu.be)


<br>


## 🛠️ Tools and structure

* **Language:** Python 3 (no external dependencies)
* **Modules:** The standard `csv` module for data management
* **Testing:** The `pytest` library for automated tests



### ⚡ Applied skills
* **File Input/Output (I/O):** Implemented stream data writing and generation of structured financial reports in CSV format.
* **Algorithms and Data Structures:** Developed custom sorting for complex collections in descending order of amounts to separate transaction types.
* **String Processing:** Designed user input parsing in an interactive CLI application.
* **Automated Testing (QA):** Covered core application functionality with unit tests using the `pytest` framework.


<br>


## Running the application

From the project folder:

```bash
python3 project.py
```

After starting the program, enter `help` to see the list of commands. The application interface is in English.



<br>



## ⚙️ Main functions

<details>
<summary><b>📂 Core Architecture</b></summary>

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

</details>


The current state is stored in two global variables:
- `balance` — the current balance;
- `history` — a list of transactions in the format `(type, amount, description)`, where the type is `"+"` for income or `"-"` for an expense.


<br>




## 💾 Export

`history.csv` contains the fields `Action`, `Amount`, `Description`, and `Balance`; `sorted.csv` contains `Action`, `Amount`, and `Description`. The final balance and average income and expense transaction amounts are added at the end of each file.


> ⚠️ **Important:** Exporting again overwrites the file with the same name. To save multiple sessions, rename or copy the results manually.


<br>




## 🧪 Tests

To run the tests, you will need `pytest` installed. Run in the console:

```bash
python3 -m pip install pytest
python3 -m pytest -q test_project.py
```


The project includes **7 automated tests** that check the core logic of adding income, withdrawing expenses, and the help text.


> ⚠️ **Important:** The export tests create `history.csv` and `sorted.csv` in the working folder and may overwrite existing files.




<br>


## Usage example

```bash
\$ python3 project.py

> add \$500 salary
[+] Added: \$500.0 (salary)

> withdraw \$125 food
[-] Withdrew: \$125.0 (food)

> print history
--- HISTORY ---
+ \$500.0 | salary
- \$125.0 | food
Current Balance: \$375.0

> export csv
[✔] Success: history.csv saved!
```




<br>


> [!WARNING]  
> **Limitations of the course project version:**
> * **Memory:** The history and balance are reset when the program exits. CSV files can be saved separately; importing them back is not implemented.
> * **Precision:** Amounts use `float`, so fractional values may have representation errors.
> * **Validation:** Input validation is incomplete: negative and special numeric values are not rejected. An unknown command terminates the program with an error.
> * **Case Sensitivity:** All input text, including transaction descriptions, is converted to lowercase.
> * **Localization:** The `$` symbol is fixed in the interface; multiple currencies and transaction dates are not supported.




<br>


## Possible improvements (Roadmap)
- [ ] Switch to `Decimal` for monetary amounts.
- [ ] Validate amounts and handle invalid commands without ending the session.
- [ ] Add saving and loading of the history between runs.
- [ ] Check the contents of the output and CSV files in tests, and isolate the state of each test.


<br>




## Files

```text
project.py          — application
test_project.py     — original tests
examples/           — sample CSV files from the course project
README.md           — description and instructions in Russian
.gitignore          — excludes temporary files and run outputs
```
