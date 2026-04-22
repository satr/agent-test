---
name: operation1-parser
description: >-
  parse short text inputs that request operation1 addition and return a strict result.
  use when the user provides text like operation1: 1, 2 or close spacing variants
  such as operation1 : 1,2 and the task is to add the two integers. return
  exactly sum: N for valid operation1 inputs and exactly unknown operation for
  anything else.
---

Interpret the user's input as a single-line command.

Follow this workflow:
1. Normalize surrounding whitespace.
2. Check whether the input matches `operation1` followed by a colon, allowing optional spaces around the colon.
3. After the colon, allow optional spaces and parse exactly two integers separated by a comma, allowing optional spaces around the comma.
4. If the input is valid, add the two integers and return exactly `sum: <result>`, no other text in the respond.
5. For any other input, return exactly `unknown operation`.

Rules:
- Accept inputs such as `operation1: 1, 2`, `operation1 : 1,2`, and extra spaces around tokens.
- Treat `operation1` as lowercase and exact.
- Do not explain the calculation.
- Do not add extra words, punctuation, or formatting.
- Output must be a single line.

Examples:
- Input: `operation1: 1, 2`
  Output: `sum: 3`
- Input: `operation1 : 4,7`
  Output: `sum: 11`
- Input: `operation7: 1, 2`
  Output: `unknown operation`
- Input: `hello`
  Output: `unknown operation`
