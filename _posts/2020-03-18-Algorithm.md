### Trie, Practice with leetcode

* Trie is a Tree structre, used for inserting and searching same string or same prefix. 

**1. Add and Search Word - Data structure design (Leetcode 211)** 

Python code:
```javascript
class TrieNode:
    def __init__(self):
        self.children = {}
        self.isend = False
    
class WordDictionary:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.root = TrieNode()
        
    def addWord(self, word: str) -> None:
        """
        Adds a word into the data structure.
        """
        node = self.root
        for w in word:
            if w not in node.children:
                node.children[w] = TrieNode()
            node = node.children[w]
        node.isend = True
        
    def search(self, word: str) -> bool:
        """
        Returns if the word is in the data structure. A word could contain the dot character '.' to represent any one letter.
        """
        if word is None:
            return False
        return self.search_helper(word,0,self.root)
    def search_helper(self,word,index,node):
        if node is None:
            return False
        if len(word)==index:
            return node.isend
        char = word[index]
        if char != '.':
            return self.search_helper(word,index+1,node.children.get(char))
        else:
            for child in node.children:
                if self.search_helper(word,index+1,node.children.get(child)):
                    return True
        return False

```
