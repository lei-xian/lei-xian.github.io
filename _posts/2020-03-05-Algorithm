### Backtracking, practice with leetcode
* Used for finding all solutions by exploring all potential candidates
* dfs

**1. Letter Combinations of a Phone Number(leeocode 17)**

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

Java code:
```javascript
class Solution {
    List<String> res = new ArrayList<String>();
    Map<String,String> KEYBOARD = new HashMap<String,String>(){{
        put("2", "abc");
        put("3", "def");
        put("4", "ghi");
        put("5", "jkl");
        put("6", "mno");
        put("7", "pqrs");
        put("8", "tuv");
        put("9", "wxyz");
    }};
    
    public void dfs(String digits, int index, String combination){
        if (index == digits.length()) res.add(combination);
        else{
            String letters = KEYBOARD.get(Character.toString(digits.charAt(index)));
            for (int i=0; i<letters.length(); i++){
                dfs(digits, index+1, combination+letters.charAt(i));
            }
        }
        
    }
    public List<String> letterCombinations(String digits) {
        if (digits.length()==0) return res;
        dfs(digits, 0, "");
        return res;
    }
}
```
