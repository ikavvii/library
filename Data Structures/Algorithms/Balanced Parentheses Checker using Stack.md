```sh
Algorithm:  CheckBalancedBrackets(string)
Input: string (containing brackets)
Output: True if balanced, False otherwise

1. Start
2. Initialize empty Stack S
3. For each character ch in string do
      If ch is opening bracket ('(', '[', '{') then
          Push ch onto Stack S
      Else if ch is closing bracket (')', ']', '}') then
          If Stack S is empty then
              Return False  // No matching opening bracket
          End If
          top = Pop from Stack S
          If top and ch are not matching pair then
              Return False  // Mismatched brackets
          End If
      End If
   End For
4. If Stack S is empty then
      Return True  // All brackets matched
   Else
      Return False  // Some opening brackets unmatched
   End If
5. Stop

Function isMatchingPair(open, close)
1. If (open == '(' AND close == ')') then Return True
2. If (open == '[' AND close == ']') then Return True
3. If (open == '{' AND close == '}') then Return True
4. Return False
```