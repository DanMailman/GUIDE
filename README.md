# MindStride Python GUIDE
**A Simple Standard for Experienced Programmers**
## INTRODUCTION & ASSUMPTIONS
1. **Polyglot Reality**<br>
   Experienced programmers use several languages, often in a single day. 
   Time spend unnecessarily making docs adhere to standards for the sake of adherence hampers productivity.
2. **Code Use and Maintenance**<br>
   Good code gets used and modified over time.  This means that code has two different audiences.
   Coders who will use it, and coders who will maintain it.  Each audience needs different information.
3. **Self-Documenting First**<br>
   Well-written code requires minimal inline or external docs.  
4. **Terse but Clear**<br>
   Well-written docs are succinct and high-impact.  
5. **Variations**<br>
   Deviate from GUIDE **only** when there is a compelling explanatory reason. 
   Use `NOTE:` to enhance the usefulness of the addition.
6. **GUIDE docs are easily distinguished from pre-existing docs**<br>
   This makes them easier to find and use.
## DOCUMENTATION (DOCS) 
### In General
- Use Line comments (#) rather than block comments to eliminate wasted vertical space
- *GUIDE avoids `"""docstrings"""` to prevent wasted vertical space.*
- Use vertical alignment of equivalent elements to enhance readability via pattern matching
- Use spacing with delimiters (#) to enhance readability.

```python
from os     import makedirs                   # makedirs(): Creates directories
from os     import path                       # path: Handles file and directory paths
from sys    import stderr                     # stderr: Outputs error messages
from sys    import exit                       # exit(): Exits the program with a status code
from typing import Dict                       # Dict: Type hint for dictionary structures
from UTILS  import GetProblemListFromFile     # GetProblemListFromFile(): Parses problem CSV into a dictionary list
from UTILS  import GetSolutionDictionaryList  # GetSolutionDictionaryList(): Processes problems with a solution function
from UTILS  import PutSolutionDictionaryList  # PutSolutionDictionaryList(): Outputs solution dictionaries to CSV
from UTILS  import OutputSolutionStatements   # OutputSolutionStatements(): Prints formatted solution statements
from UTILS  import PrintDictionaryList        # PrintDictionaryList(): Output dictionaries in a list in readable format.
from UTILS  import GetSolutionStatements      # GetSolutionStatements(): Generate solution statements using the provided function.
from UTILS  import GenerateGraphsPDF          # Creates a PDF with plots for given problems.
k_sProblemFolder  = 'PROBLEMS'
k_sSolutionFolder = 'SOLUTIONS'
k_sProblemFile    = 'Ex01_01_Problems.csv'
k_sSolutionFile   = 'Ex01_01_Solutions.csv'
k_sStatementsFile = 'Ex01_01_Statements.csv'
k_sGraphsFile     = 'Ex01_01_Graphs.pdf'
```
### File Docs
- The first line in a file is **always** the precise filename with a single, concise usage line.<br>
- The second line is **always** the author
- The third line is **always** the date
- An optional fourth line may be required for license information
- Additional, `NOTE:` lines only to call attention to special features, or information useful to understanding the code. 
```python
# Ex01_01_Solver_Mailman.py: Produces CSV of Solutions to Braking Problems in CSV
# Dan Mailman
# 22jan25
# NOTE: Implements type checking, error handling, configurable paths, and .txt output
```
### Imports Docs
- One line for each type (class), function, or constant used from each package followed by a terse, comment
```python
from os import makedirs                      # makedirs(): Creates directories
from os import path                          # path: Handles file and directory paths
from sys import stderr                       # stderr: Outputs error messages
from sys import exit                         # exit(): Exits the program with a status code
from typing import Dict                      # Dict: Type hint for dictionary structures
from UTILS import GetProblemListFromFile     # GetProblemListFromFile(): Parses problem CSV into a dictionary list
from UTILS import GetSolutionDictionaryList  # GetSolutionDictionaryList(): Processes problems with a solution function
from UTILS import PutSolutionDictionaryList  # PutSolutionDictionaryList(): Outputs solution dictionaries to CSV
from UTILS import OutputSolutionStatements   # OutputSolutionStatements(): Prints formatted solution statements
from UTILS import PrintDictionaryList        # PrintDictionaryList(): Output dictionaries in a list in readable format.
from UTILS import GetSolutionStatements      # GetSolutionStatements(): Generate solution statements using the provided function.
from UTILS import GenerateGraphsPDF          # Creates a PDF with plots for given problems.
```
### Function/Method Docs
- The **FileDocs** or **MethodDocs** are two single-line comments:
  - The **Usage Line** tells users of the function/method what it does when used in code
  - The **Implementation Line** tells maintainers of the function/method what they need to know to maintain/change the code.
### Inline Docs
- Good code is self-documenting. So, additional comments hinder productivity by wasting reader scan.
- Inline comments are reserved for supplementary explanation that saves programmer time.
## IDENTIFIER NAMING 
### In General
- To minimize reader scan, use as few characters as possible for identifiers.
- Use capitalization to distinguish (e.g.) words or abbreviations in identifiers. (e.g., `GetSolutionDictionary`)
- Use underscores (e.g. snake case) only to enhance readability.
> ✅ `Build_HTTP_Request`  
> ✅ `BuildRequestHTTP`  
> ❌ `BuildHTTPRequest`  
### File Names
- Use descriptive and concise PascalCase file names. (e.g., `ProcessBrakingData.py`).
- Drafts of program/module/class files may be appended with author name(e.g., `ProcessBrakingData_Mailman.py`).
### Function/Method Names
- Use descriptive and concise PascalCase file names (e.g., `GetSolutionDictionary()`, `PrintSolutionStatements()`).
- **`main()`** is an exception and remains lowercase to meet expectations of experienced programmers.
### Variable Names
#### Variable Names Use Type-Prefixed PascalCase
- Variables are named with **Type-Prefixed PascalCase**. 
- three or fewer lowercase letters for the type
  - `n` for numbers (integer or float) used for value (e.g. `nCount = 5`, `nTemperature = 32.6`)
  - `i` for integers used for iteration in loops (e.g., `for iPerson in range(nPersons):`)
  - `s` for strings (e.g. 
  - `t` for types (classes in python). (e.g., `tPerson`)
  - `o` for objects (e.g. `oPerson01 = tPerson('bob')`)
#### Optional Convention for Types (Classes)
  - Three letter acronyms for objects of the type (e.g. `prsBob = tPerson('bob')`)
#### Additional prefix for constants
- Variables used as constants are prefixed by `k_` (e.g., `k_nMaxRetries`).
- This enhances readability especially when constants are grouped together.
```python
k_sProblemFolder  = 'PROBLEMS'
k_sSolutionFolder = 'SOLUTIONS'
k_sProblemFile    = 'Ex01_01_Problems.csv'
k_sSolutionFile   = 'Ex01_01_Solutions.csv'
k_sStatementsFile = 'Ex01_01_Statements.csv'
k_sGraphsFile     = 'Ex01_01_Graphs.pdf'
```
## SPACING & LAYOUT
- **Vertical Space is Gold**  
  - Insert blank lines *only* to delineate significant logic sections.  
  - Too many significant logic sections indicates the need for subordinate functions.
- **Line Length**  
  Keep lines comfortably short (~80–100 characters).  
- **Indentation**  
  Use 4 spaces (no tabs).  
- **Docstrings**  
  Exclude unless explicitly required by the project. They add extra blank lines in many Python code editors—GUIDE avoids that clutter.
## PROGRAM STRUCTURE
### RECOMMENDATIONS
- run-time constants grouped immediately after imports to make them easier to find in reader scan  
  since they are likely to be modified often
### Group Standard vs. Local Imports
Use line comments to Separate imports by class (standard, third‑party, local)
```python
# Standard Library Imports 
from os       import path             # path: File and directory path manipulations
from sys      import exit             # exit: Terminate the program gracefully
#  Third-Party Imports 
from numpy    import array            # array: High-performance array operations
from pandas   import DataFrame        # DataFrame: 2D labeled data structure for data analysis
#  Local Imports 
from mymodule import my_function      # my_function: Custom business logic from mymodule
from utils    import helper_function  # helper_function: Utility for additional support tasks
```
## DEVIATIONS FROM COMMON PYTHON PRACTICES
These divergences are intentional design choices aligned with GUIDE’s goal of speed and clarity 
for experienced and polyglot programmers frequently switching between languages.
### Excluding `"""docstrings"""`
Typical Python convention (PEP 257) favors docstrings for automated documentation and code introspection.  
GUIDE consciously eliminates them to preserve vertical space for experienced and polyglot programmers.
### Type‑Prefixed Variables
Python’s flexibility (dynamic typing) and PEP 8 typically do not enforce Hungarian‑style notation.  
GUIDE explicitly uses a short type prefix (e.g., `nCount`), prioritizing quick scan for multi‑language developers.
### Inline Documentation in Imports
Python style guides usually group imports at the top with minimal or no inline commentary.  
GUIDE invests in alignment and commentary for clarity, 
especially for experienced and polyglot programmers or large codebases.

### Use of PascalCase for Functions/Methods
PEP 8 encourages `snake_case` for function names.  
GUIDE standardizes on PascalCase to facilitate rapid scanning in polyglot environments 
where CamelCase/PascalCase is common.

### Constants Not in ALL_CAPS
Python typically uses uppercase for constants.  
GUIDE uses `k_` prefix with PascalCase (e.g., `k_sProblemFile`). Again, it’s a deliberate choice for visual scanning.

## CONCLUSION
GUIDE aims to empower experienced developers by maximizing clarity and minimizing boilerplate. 
Any variation from these guidelines should be called out explicitly and reserved for compelling cases. 
The result: code that is uniformly legible, easy to maintain, and efficient to scan for polyglot programmers.
