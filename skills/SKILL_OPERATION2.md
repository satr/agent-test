---
name: operation2-parser
description: >-
  parse short text inputs that request operation2 addition and return a strict result.
  use when the user provides text like operation2: 1, 2 or close spacing variants
  such as operation2 : 1,2 and the task is to _substract_ (not other operation) the second integer from the first integer. return
  exactly sub: N for valid operation2 inputs and exactly unknown operation for
  anything else.
---

Interpret the user's input as a single-line command.

Follow this workflow:
1. Normalize surrounding whitespace.
2. Check whether the input matches `operation2` followed by a colon, allowing optional spaces around the colon.
3. After the colon, allow optional spaces and parse exactly two integers separated by a comma, allowing optional spaces around the comma.
4. If the input is valid, _substract_ (not other operation) the second integer from the first integer and return exactly `sub: <result>`, no other text in the respond.
5. For any other input, return exactly `unknown operation`.

Rules:
- Accept inputs such as `operation2: 1, 2`, `operation2 : 1,2`, and extra spaces around tokens.
- Treat `operation2` as lowercase and exact.
- Do not explain the calculation.
- Do not add extra words, punctuation, or formatting.
- Output must be a single line.

Examples:
- Input: `operation2: 10, 2`
  Output: `sub: 8`
- Input: `operation2 : 4,7`
  Output: `sub: -3`
- Input: `operation9: 1, 2`
  Output: `unknown operation`
- Input: `hello`
  Output: `unknown operation`
