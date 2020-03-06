## Backtracking, practice with leetcode
* Used for finding all solutions by exploring all potential candidates
* dfs

1. Letter Combinations of a Phone Number(leeocode 17)

* use a backtrack function backtrack(combination, next_digits)
  - base case: if there is no more next digits to check means the current combination is done
  - otherwise: iterate over the char and mapping next available digit.
    - append current char to current combination 
    - index+1 to check next digit
    
Python code: 
```javascript
KEYBOARD = {
    '2': 'abc',
    '3': 'def',
    '4': 'ghi',
    '5': 'jkl',
    '6': 'mno',
    '7': 'pqrs',
    '8': 'tuv',
    '9': 'wxyz',
}
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        results = []
        if not digits: return results
        self.dfs(digits,0,'',results)
        return results
    def dfs(self, digits, index, string, results):
        if index == len(digits):
            results.append(string)
            return
        else:
            for char in KEYBOARD[digits[index]]:
                self.dfs(digits, index+1, string+char, results)
```
