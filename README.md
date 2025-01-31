# MindStride Python GUIDE
**A Proposed Universal Standard for Experienced Programmers**
## INTRODUCTION & ASSUMPTIONS
1. **Polyglot Reality**  
   Experienced programmers use several languages, often in a single day. 
   Time spend unnecessarily making docs adhere to standards for the sake of adherence hampers productivity.
2. **Code Use and Maintenance**
   Good code gets used and modified over time.  This means that code has two different audiences.
   Coders who will use it, and coders who will maintain it.  Each audience needs different information.
3. **Self-Documenting First**  
   Well-written code requires minimal inline or external docs.  
4. **Terse but Clear**  
   Well-written docs are succinct and high-impact.  
5. **Variations**  
   Deviate from GUIDE **only** when there is a compelling explanatory reason. 
   Use `NOTE:` to enhance the usefulness of the addition.
6. **GUIDE docs are easily distinguished from pre-existing docs**
   This makes them easier to find and use.
## DOCUMENTATION (DOCS) 
### In General
- Use Line comments (#) rather than block comments to eliminate wasted vertical space
- *GUIDE avoids `"""docstrings"""` to prevent wasted vertical space.*
- Use vertical alignment of equivalent elements to enhance readability via pattern matching
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
- Use underscores (e.g. snake case) only to enhance readability.  (e.g., `Build_HTTP_Request` or `BuildRequestHTTP`) 
### File Names
- Use descriptive and concise PascalCase file names. (e.g., `ProcessBrakingData.py`).
- Drafts of program/module/class files may be appended with author name(e.g., `ProcessBrakingData_Mailman.py`).
### Function/Method Names
- Use descriptive and concise PascalCase file names (e.g., `GetSolutionDictionary()`, `PrintSolutionStatements()`).
- main() is an exception and remains lowercase to meet expectations of experienced programmers.
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

#### Type Indicator Prefixes
- Indicate the type of the variable with a prefix.
  - `n` for time-related variables (e.g., `t1`, `t2`).
## SPACING & LAYOUT
- **Vertical Space is Gold**  
  Insert blank lines *only* to delineate significant logic sections.  
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
## CONCLUSION
GUIDE aims to empower experienced developers by maximizing clarity and minimizing boilerplate. 
Any variation from these guidelines should be called out explicitly and reserved for compelling cases. 
The result: code that is uniformly legible, easy to maintain, and efficient to scan for polyglot programmers.
