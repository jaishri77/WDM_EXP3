### EX3 Implementation of GSP Algorithm In Python
### DATE:  7/2/26
### AIM: To implement GSP Algorithm In Python.
### Description:
The Generalized Sequential Pattern (GSP) algorithm is a data mining technique used for discovering frequent patterns within a sequence database. It operates by identifying sequences that frequently occur together. GSP works by employing a depth-first search strategy to explore and extract frequent patterns efficiently.
### Steps:
1. <strong>Database Scanning:</strong> GSP scans the sequence database to determine the support of each item in the dataset.
2. <strong>Candidate Generation:</strong> It generates a set of candidate sequences using frequent items found in the previous step.
3. <strong>Pattern Growth:</strong> It extends the candidate sequences by merging them to form longer patterns, checking their support against a user-defined minimum support threshold.
4. <strong>Repeat:</strong> The process continues until no new sequences meet the minimum support threshold.
<p align="justify">
GSP finds application in various domains such as market basket analysis, web usage mining, bioinformatics, and more. For instance, in retail, GSP can identify common purchasing patterns, helping businesses understand customer behavior for targeted marketing or inventory management.
</p>

### Procedure:
<p align="justify">
1. From collections import defaultdict, from itertools import combinations: Imports necessary libraries/modules. defaultdict is
used to create a dictionary with default values and combinations generates all possible combinations of a sequence.</p>
<p align="justify">
2. generate_candidates(dataset, k): Function to generate candidate k-item sequences from a dataset. It loops through each sequence in the
dataset and finds combinations of length k for each sequence, updating their counts in a dictionary.</p>
<p align="justify">
3. gsp(dataset, min_support): Function that implements the Generalized Sequential Pattern (GSP) algorithm. It iterates through increasing
sequence lengths (k) until no new frequent patterns are found. It calls generate_candidates() to find patterns of varying lengths.</p>
<p align="justify">
4. Example dataset for each category: Defines example sequences for top wear, bottom wear, and party wear categories.</p>
<p align="justify">
5. Minimum support threshold: Sets the minimum support count required for a pattern to be considered frequent.</p>
<p align="justify">
6. Perform GSP algorithm for each category: Applies the GSP algorithm for each category using the defined example datasets and the
minimum support threshold.</p>
<p align="justify">
7. Output the frequent sequential patterns for each category: Prints the frequent sequential patterns 
    along with their support counts
for each wear category.</p>
<p align="justify">
8. Visulaize the sequence patterns using matplotlib.
</p>
### Program:

```python
]from collections import defaultdict
from itertools import combinations
from tabulate import tabulate  # For table formatting

# Function to generate candidate k-item sequences
def generate_candidates(dataset, k, min_support):
    candidates = defaultdict(int)
    for seq in dataset:
        for comb in combinations(seq, k):
            candidates[comb] += 1
    return {item: support for item, support in candidates.items() if support >= min_support}

# Function to perform GSP algorithm
def gsp(dataset, min_support):
    frequent_patterns = defaultdict(int)
    k = 1
    sequences = dataset
    while True:
        candidates = generate_candidates(sequences, k, min_support)
        if not candidates:
            break
        frequent_patterns.update(candidates)
        k += 1
    return frequent_patterns

# Example dataset for each category
top_wear_data = [
    ['a','b','c','b','e','c','f','g','a','b','c'],
    ['a','d','b','c','c','f','g','c','h'],
    ['b','c','a','d','e','b','f','c','d','f','g','h'],
    ['c','e','c','e','h']
    # Add more sequences for top wear
]

# Minimum support threshold
min_support = 4

# Perform GSP algorithm for each category
top_wear_result = gsp(top_wear_data, min_support)

# Output the frequent sequential patterns for each category in table format
print("Frequent Sequential Patterns - Top Wear:")
if top_wear_result:
    table_data = []
    for pattern, support in top_wear_result.items():
        table_data.append([pattern, support])
    print(tabulate(table_data, headers=["Pattern", "Support"], tablefmt="grid"))
else:
    print("No frequent sequential patterns found in Top Wear.")
```
### Output:
<img width="1321" height="961" alt="image" src="https://github.com/user-attachments/assets/2bcf95dd-5bf1-4d89-81db-a97ea9062350" />
<img width="1325" height="982" alt="image" src="https://github.com/user-attachments/assets/cdbfed65-f088-4f99-a9f0-7a4467af1f6c" />
<img width="1278" height="938" alt="image" src="https://github.com/user-attachments/assets/f0c801ff-6b74-4c0e-b0a9-419840e65d7d" />


### Result:
GSP Algorithm In Python is implemented successfully.
