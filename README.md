# C++ Custom Utility Libraries & OOP Implementation

A practical implementation of reusable, **Header-Only Utility Libraries** built in C++ using Object-Oriented Programming (OOP) and Clean Code practices. 

This project was built as part of Course 10 in Dr. Mohammed Abu-Hadhoud's software engineering roadmap, focusing on eliminating code duplication (DRY principle) for common tasks like string parsing, calendar math, and input validation.

---

## 📁 Project Architecture

The library follows a **Header-Only** design pattern for quick integration into future projects without extra `.cpp` compilation setup:

* `clsString.h` — Handles string manipulation, tokenization, and formatting.
* `clsDate.h` — Manages complex date operations, leap year logic, and date arithmetic.
* `clsInputValidate.h` — Acts as a validation layer relying on both date and string libraries.
* `Certificate.pdf` — Course completion certificate.

---

## ⚙️ Technical Overview & Features

### 1️⃣ String Utility (`clsString`)
Provides both static and instance-level utilities for advanced string processing:
* **Parsing & Splitting:** Breaks strings into `std::vector<string>` based on custom delimiters.
* **Case Transformations:** Capitalizes words, converts full text to Upper/Lower case.
* **Cleaning & Counting:** Trimming whitespace, counting specific characters or words with case-sensitivity options.

### 2️⃣ Date Utility (`clsDate`)
Handles date calculations and time-based operations accurately:
* **Date Difference:** Calculates exact days between two dates considering leap years.
* **Calendar Math:** Adds days/weeks/months/years to a date and determines the day of the week.
* **Validation:** Checks if a given day/month/year combination forms a valid date.

### 3️⃣ Input Validation (`clsInputValidate`)
Serves as a robust defense layer against unexpected user input:
* **Range Checks (`IsNumberBetween`):** Validates integers and floating-point numbers against specified bounds.
* **Date Bounds (`IsDateBetween`):** Validates if a target date falls within a given date range using `clsDate`.
* **Buffer-Safe Reading:** Handles type mismatch errors during console input, clearing stream buffers cleanly until valid data is entered.

---

## 🔗 Dependency Structure

The modules are built with a clear dependency order to simplify imports:

`clsInputValidate.h` ➡️ Depends on ➡️ `clsDate.h` + `clsString.h`

Including `clsInputValidate.h` in your `main.cpp` automatically brings in the other utilities. All headers use `#pragma once` to prevent redefinition issues.

---

## 📜 Certification

The verified completion certificate for Course 10 is available in this repository:
👉 **`Certificate.pdf`**

---

## 🚀 Quick Usage Example

```cpp
#include <iostream>
#include "clsInputValidate.h"

int main() {
    int age = clsInputValidate::ReadIntNumberBetween(18, 60, "Invalid Age! Please enter between 18 and 60: ");
    std::cout << "Valid Age Entered: " << age << std::endl;
    return 0;
}
