---
title: Astro
permalink: /astro/
sitemap: false
---

# 2024 Log on Astro and AstroPaper

### 6/19/2024
* See dialog in ChatGPT with suggested Astro code.

### 6/20/2024 - intro to JavaScript before Astro
* Created dev.to account and found this April, 2024 [article](https://dev.to/snikidev/astrojs-as-an-alternative-to-nextjs-pushing-the-limits-30ga) by Nikita Kakuev on how the Astro approach (if not necessarily the Astro framework) is the future. "The future is simple, vanilla JS because simplicity always wins."

#### datastructures
* Table comparing the names used in various languages for common data structures

|             | **Array**    | **Map**          | **Set**       |
|-------------|--------------|------------------|---------------|
| **JavaScript** | array        | map              | set           |
| **Python**     | list         | dict             | set           |
| **Java**       | Array / ArrayList | HashMap          | HashSet       |
| **Computer Science**         | Dynamic Array | Hash Table / Associative Array / Dictionary | Hash-Set      |

#### explanation of differences between JS and Python for arrays, maps, and sets
Here are the definitions for the specified items along with their equivalent data structures or objects in Python, including differences:

1. **Array**
	*  **JavaScript Definition:** An `Array` is an ordered collection of values (elements) that are indexed by integers. Each element in an array has a specific position, starting from index 0. Arrays can store elements of any type, including other arrays, objects, or primitive values.
		*  **Example:**
		     ```javascript
		     let fruits = ["apple", "banana", "cherry"];
		     console.log(fruits[1]); // Output: banana
		     ```
	* **Python Equivalent:** `list`
		* **Definition:** A `list` in Python is an ordered collection of elements that can be of any type. Lists are indexed by integers, starting from index 0, similar to JavaScript arrays.
		* **Example:**
		       ```python
		       fruits = ["apple", "banana", "cherry"]
		       print(fruits[1]) # Output: banana
		       ```
	* **Differences:** Python lists can also hold elements of any type, including other lists and objects, just like JavaScript arrays. Both data structures are dynamic in size and allow for element modifications.

2. **Map**
	*  **JavaScript Definition:** A `Map` is a collection of key-value pairs where both keys and values can be of any type. Unlike plain objects, which use strings as keys, maps can use objects, functions, and other data types as keys. Maps maintain the order of their elements based on the order of insertion.
		* **Example:**
			```javascript
			let map = new Map();
			map.set('name', 'Alice');
			map.set('age', 30);
			console.log(map.get('name')); // Output: Alice
			```
	* **Python Equivalent:** `dict`
		* **Definition:** A `dict` (dictionary) in Python is a collection of key-value pairs where keys can be of any immutable type (e.g., strings, numbers, tuples), and values can be of any type. Dictionaries maintain insertion order since Python 3.7.
		* **Example:**
		```python
		info = {'name': 'Alice', 'age': 30}
		print(info['name']) # Output: Alice
		```
	* **Differences:** Python dictionaries only allow immutable types as keys, while JavaScript maps allow any type of keys. Both structures maintain insertion order and allow for dynamic addition and modification of elements.

3. **Set**
	* **JavaScript Definition:** A `Set` is a collection of unique values. Unlike arrays, sets do not allow duplicate elements. Sets can store values of any type and maintain the order of insertion.
		* **Example:**
		```javascript
		let set = new Set();
		set.add(1);
		set.add(2);
		set.add(2); // Duplicate value, won't be added
		console.log(set.size); // Output: 2
		```
	* **Python Equivalent:** `set`
		* **Definition:** A `set` in Python is an unordered collection of unique elements. Sets do not allow duplicate values and can store elements of any immutable type.
		* **Example:**
		```python
		s = set()
		s.add(1)
		s.add(2)
		s.add(2) # Duplicate value, won't be added
		print(len(s)) # Output: 2
		```
	* **Differences:** Both JavaScript sets and Python sets store unique values and do not allow duplicates. JavaScript sets maintain insertion order, while Python sets are unordered collections. Both support basic set operations like union, intersection, and difference.


***

# AstroPaper 2025 Log
## 1/11/2025
* Installed v4.0 version of Astro. Install instructions from Astro 3 [blog post](https://astro-paper.pages.dev/posts/astro-paper-v3/)

