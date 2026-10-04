# CS 3110 — NFA Design 1

This repository documents my process of designing, testing, debugging, and reflecting on nondeterministic finite automata using JFLAP.

## Selected Problems

| Problem | Language                                           | Status    |
| ------- | -------------------------------------------------- | --------- |
| 6       | Strings that start with `10`                       | completed |
| 7       | Strings that end with `10`                         | completed |
| 9       | Strings that contain substring `10`                | completed |
| 11      | Strings whose second-to-last bit is `1`            | completed |
| 20      | Strings with `3k+1` ones or an odd number of zeros | completed |

## Repository Files

Each problem includes:

- `nXX.jff` — JFLAP NFA file
- `nXXt.txt` — accepted and rejected test strings
- `nXXr.md` — NFA image, test evidence, debugging, and reflection

Problems 7, 9, and 11 also include step-by-step JFLAP screenshots and hand-drawn computation trees.

## Learning Summary

### Most Challenging Problems

Problem 11 was challenging because I had to understand how the NFA could guess which `1` was the second-to-last symbol. I learned that a wrong branch can die while another branch continues and accepts.

Problem 20 was also challenging because it combines two different conditions with OR. I used epsilon transitions to split the NFA into one branch that counts `1`s modulo 3 and another branch that tracks whether the number of `0`s is odd.

### Gold Strings and Debugging

Some strings helped me understand and debug the NFAs:

- `110` for problem 7 showed that one branch can die while another path still accepts.
- `101` for problem 11 helped confirm that reaching the accepting state too early should not accept the string.
- `000111` for problem 11 showed how the NFA can keep scanning until it guesses the correct second-to-last `1`.
- For problem 20, I tested strings that satisfied only one side of the OR and strings that satisfied neither condition.

These tests helped me find mistakes in my transitions and understand why each NFA worked.

### Insights and Questions

The biggest thing I learned is that an NFA does not require every path to succeed. A string is accepted as long as at least one path consumes the full input and ends in an accepting state.

I also learned that epsilon transitions can be used to combine multiple NFAs, especially when the language uses an OR condition.

Drawing computation trees helped me see the different paths more clearly and understand when branches die.
