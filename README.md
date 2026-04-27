# Employee File Processing System (COBOL)

## Table of Contents

* [Overview](#overview)
* [Programs Included](#programs-included)

  * [SEQ3000 - Sequential File Update](#seq3000---sequential-file-update)
  * [EMPIND1 - Create Indexed File](#empind1---create-indexed-file)
  * [EMPIND2 - Indexed File Maintenance](#empind2---indexed-file-maintenance)
* [File Structures](#file-structures)
* [How It Works](#how-it-works)
* [Input and Output Files](#input-and-output-files)
* [How to Run](#how-to-run)
* [Error Handling](#error-handling)
* [Author](#author)

---

## Overview

This project contains three COBOL programs that simulate an employee database system.
The system reads transaction records and applies them to a master employee file using both sequential and indexed file processing techniques.

---

## Programs Included

### SEQ3000 - Sequential File Update

This program updates a sequential employee master file using a transaction file.

**Features:**

* Processes Add (A), Change (C), and Delete (D) transactions
* Matches transaction records with master records
* Writes updated records to a new master file
* Logs invalid transactions to an error file

---

### EMPIND1 - Create Indexed File

This program converts a sequential employee master file into an indexed file.

**Features:**

* Reads sequential records
* Writes them into an indexed file structure
* Uses Employee ID as the record key

---

### EMPIND2 - Indexed File Maintenance

This program updates an indexed employee file using random access.

**Features:**

* Supports Add, Change, and Delete operations
* Uses direct access via Employee ID
* Performs faster updates compared to sequential processing
* Writes invalid transactions to an error file

---

## File Structures

### Employee Master Record

* Employee ID (5 characters)
* Name (30 characters)
* Department Code (5 characters)
* Job Class (2 characters)
* Annual Salary (numeric)
* Vacation Hours
* Sick Hours

### Transaction Record

* Transaction Code (A, C, D)
* Employee Data Fields

---

## How It Works

1. **SEQ3000**

   * Reads both master and transaction files in order
   * Compares Employee IDs
   * Applies updates sequentially

2. **EMPIND1**

   * Converts sequential file into indexed format

3. **EMPIND2**

   * Uses indexed file for direct access updates
   * Improves efficiency over sequential processing

---

## Input and Output Files

| File Name | Description                      |
| --------- | -------------------------------- |
| EMPTRAN   | Transaction input file           |
| OLDEMP    | Original master file             |
| NEWEMP    | Updated master file (sequential) |
| EMPMASTI  | Indexed master file              |
| ERRTRAN   | Error transaction file           |

---

## How to Run

1. Compile each COBOL program:

   ```
   cobc -x SEQ3000.cbl
   cobc -x EMPIND1.cbl
   cobc -x EMPIND2.cbl
   ```

2. Run programs in order:

   ```
   ./SEQ3000
   ./EMPIND1
   ./EMPIND2
   ```

---

## Error Handling

* Invalid transactions are written to `ERRTRAN`
* File status codes are checked after writes
* Program stops if critical file errors occur

---

## Author

Garrett Finke
CIS 352
March 2026
