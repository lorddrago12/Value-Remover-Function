# 🗑️ Value Remover Function

A lightweight JavaScript utility that removes specified values from an array, returning a clean copy with those elements filtered out.

---

## Overview

`destroyer` takes an array and any number of values to remove, then returns a new array with all matching elements excluded. The original array is never mutated.

---

## Usage

```js
function destroyer(arr, ...removeValues) {
  return arr.filter(item => !removeValues.includes(item));
}
```

### Example

```js
destroyer([1, 2, 3, 1, 2, 3], 2, 3);
// → [1, 1]

destroyer(['a', 'b', 'c', 'a'], 'b');
// → ['a', 'c', 'a']

destroyer([true, false, true, null], false, null);
// → [true, true]
```

---

## Parameters

| Parameter       | Type    | Description                                      |
|----------------|---------|--------------------------------------------------|
| `arr`           | `Array` | The source array to filter                       |
| `...removeValues` | `any` | One or more values to remove from the array     |

**Returns:** A new `Array` with all specified values removed.

---

## How It Works

1. The function accepts a source array as its first argument.
2. Any additional arguments are collected into `removeValues` via the rest parameter (`...`).
3. `Array.prototype.filter` iterates over `arr`, keeping only elements **not** found in `removeValues` (checked with `Array.prototype.includes`).
4. A new array is returned — the original is untouched.

---

## Notes

- Uses **strict equality** (`===`) under the hood via `includes`, so `destroyer([1, '1'], 1)` only removes the number `1`, not the string `'1'`.
- Works with any data type: numbers, strings, booleans, `null`, etc.
- Returns an **empty array** if all elements match the remove values.

---

## Compatibility

| Environment | Support |
|-------------|---------|
| Node.js     | ✅ v6+  |
| Chrome      | ✅      |
| Firefox     | ✅      |
| Safari      | ✅      |
| Edge        | ✅      |

> Requires ES6+ for rest parameters (`...`) and `Array.prototype.includes`.
