---
id: a9254c14-fd25-4d81-b0e9-57652226ffed
title: Python
desc: ''
updated: 1627958321840
created: 1609632400175
---

- raw format strings are useful when composing regex patterns in verbose mode
  ```python
  import re
  
  pattern = rf"""
  ^[{prefix}]?     # optionally match prefix at start
  (?P<all>         # capture named group all
      (?P<left>    # capture named group left
          \d+?     # lazily match digits
      )
      {infix}      # match infix
      (?P<right>   # capture named group right
          \d+      # match digits
      )
  )
  [{suffix}]?$     # optionally match suffix at start
  """

  rx = re.compile(pattern, re.VERBOSE)

  match = rx.match(some_string)
  ```
- testing out python regex
  [pythex](https://pythex.org/)

