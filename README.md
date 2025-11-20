# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1:
Count the occurrences of each unique character in the input string. Sort them by frequency.
<br>

### Step2:
Treat each character and its frequency as a leaf node in a priority queue.
<br>

### Step3:
Extract the two nodes with the lowest frequencies. Combine them into a new parent node.
<br>

### Step4:
Insert the new parent node back and repeat step 3 until only one root node remains in the list.
<br>

### Step5:
Traverse the tree (left='0', right='1'). Generate codes and print the character mapping.
<br>

 
## Program:

``` Python
# Get the input String

string = "VARNIKA P"

# Create tree nodes

class NodeTree(object):
    def __init__(self, left=None, right=None):
        self.left = left
        self.right = right
    def children(self):
        return (self.left, self.right)
    def node(self):
        return (self.left, self.right)
    def __str__(self):
        return "NodeTree({}, {})".format(self.left, self.right)


# Main function to implement huffman coding

def huffman_code_tree(node, left=True, binString=''):
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    d = dict()
    d.update(huffman_code_tree(l, True, binString + '0'))
    d.update(huffman_code_tree(r, False, binString + '1'))
    return d

# Calculate frequency of occurrence

freq = {}
for c in string:
    if c in freq:
        freq[c] += 1
    else:
        freq[c] = 1
freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)
nodes=freq
while len(nodes)>1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree (key1, key2)
    nodes.append((node,c1 + c2))
    nodes = sorted (nodes, key=lambda x: x[1], reverse=True)

# Print the characters and its huffmancode

huffmanCode = huffman_code_tree(nodes[0][0])

print(' Char | Huffman code ')
print('----------------------')
for (char, frequency) in freq:
    print('%-6r|%12s'%(char,huffmanCode[char]))


```
## Output:

### Print the characters and its huffmancode
<img width="208" height="198" alt="image" src="https://github.com/user-attachments/assets/11fc83c0-1195-48e8-99b2-7c68e4b47aac" />

<br>



## Result
Thus the huffman coding was implemented to compress the data using python programming.
