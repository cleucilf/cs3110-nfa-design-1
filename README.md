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

Some strings helped me find mistakes and understand the NFAs better.

For problem 7, `110` helped me see that an NFA can have a branch die while another branch still accepts.

For problem 11, `101` and `000111` were useful for debugging. While drawing the computation tree for `000111`, I initially did not include every next state from `q0` when reading a `1`. I forgot that `q0` could both stay in `q0` and branch to `q1`.

The mistake happened because I was following one path at a time instead of keeping track of the complete set of possible next states.

In future state-machine problems, I can avoid this by checking every transition from every currently active state before moving to the next input symbol. This is important not only for NFAs, but also for future compiler, controller, and exam problems involving states.

### Insights and Questions

Problem 11 gave me trouble because I had to understand how the NFA could guess which `1` was the second-to-last symbol.

Problem 20 was also challenging because it combines two different conditions using OR. I used epsilon transitions to separate the two conditions.

I did not avoid any of the five problems I selected. I used AI to ask questions and get guidance when I was confused, especially while debugging computation trees and understanding nondeterministic branching.
