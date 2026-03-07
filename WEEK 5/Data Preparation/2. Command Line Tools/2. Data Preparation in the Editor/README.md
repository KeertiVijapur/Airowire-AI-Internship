# Data Preparation in the Editor (https://www.youtube.com/watch?v=99lYu43L9uM)

This section demonstrates how **text editors like Visual Studio Code** can be used for quick data preparation and cleaning. Editors provide powerful features such as **formatting, multi-cursor editing, search & replace, sorting, and duplicate removal**, which make it possible to process datasets efficiently without writing code.

The example dataset used here is a **JSON file** containing records of city-wise product sales.

Example record:

```json
{
  "city": "Rio de Janeiro",
  "product": "Bananas",
  "sales": 22
}
````

Each entry contains:

* **city**
* **product**
* **sales**

---

## 1. Formatting JSON Data

Raw JSON data may not be easy to read. In Visual Studio Code, the **Format Document** feature helps automatically structure the file.

Steps:

1. Open the file in VS Code.
2. Press **Ctrl + Shift + P**.
3. Select **Format Document**.

This converts compact JSON into a readable structure with proper indentation.

---

## 2. Extracting Fields with Multi-Cursor

VS Code supports **multi-cursor editing**, which allows selecting and editing multiple occurrences of text simultaneously.

Example: Extract all city values.

Steps:

1. Select the word **city**.
2. Press **Ctrl + D** to select additional matches.
3. Extend the selection using **Shift + Arrow** or **Shift + End**.
4. Copy the selected values and paste them into a new file.

Another method:

* Use **Ctrl + F** to search for `city`.
* Press **Alt + Enter** to select all matches.
* Copy all selected values at once.

This technique quickly extracts specific fields from structured data.

---

## 3. Sorting Values

To organize extracted values:

1. Open **Command Palette** (`Ctrl + Shift + P`)
2. Select **Sort Lines Ascending**

This arranges the data alphabetically, making it easier to analyze.

---

## 4. Removing Duplicate Entries

After sorting, duplicate values can be removed.

Steps:

1. Open **Command Palette**
2. Select **Delete Duplicate Lines**

This leaves only unique values in the dataset.

---

## 5. Cleaning Data with Search & Replace

Search and replace can be used to correct inconsistencies.

Example:
Different variations of the same city name such as:

```
Bangalor
Bangalore
Bengaluru
```

Steps:

1. Use **Ctrl + F** to search for variations.
2. Press **Alt + Enter** to select all matches.
3. Use **multi-cursor editing** to replace them with a standardized value.

Example replacement:

```
Bangalore
```

All occurrences are updated simultaneously.

---

## Key Features Used

Visual Studio Code capabilities used for data preparation:

* JSON **Format Document**
* **Find and Select All** matches
* **Multi-cursor editing**
* **Sorting lines**
* **Deleting duplicate lines**
* **Batch text replacement**
