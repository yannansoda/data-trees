---
{"topic":"SoftwareEngineering, Data Science","dg-publish":true,"permalink":"/Notes/Software Engineering for DS/","dgPassFrontmatter":true,"noteIcon":""}
---

>[!Source]
>*[[BookNotes/Software Engineering for Data Scientists\|Software Engineering for Data Scientists]]*, Catherine Nelson, April 2024, O'Reilly Media, Inc. 
## How to analyze code performance
### Find bottlenecks
- timing the code
- profiling the code
	- use profiler to get the time breakdown of a script
### Handle runtime time complexity
- time complexity: how the running time of an algorithm grows as the size of the input increases
- **Big O Notation**: the runtime is described as a function of the size of the input, $n$: $O(f(n))$
	- $O(1)$ means constant time
- think about 
	- the number of steps the code will take
	- how this will scale as the amount of data grows

## Using Data Structures Effectively
| Operation         | List       | Tuple             | Dict        | Set               | NumPy Array | pandas DataFrame               |
| ----------------- | ---------- | ----------------- | ----------- | ----------------- | ----------- | ------------------------------ |
| Index Lookup      | Yes (O(1)) | Yes (O(1))        | No          | No                | Yes (O(1))  | Yes (fast)                     |
| Key Lookup        | No (O(n))  | No (O(n))         | Yes (O(1))  | Yes (O(1))        | No (O(n))   | Yes (fast)                     |
| Search by Value   | No (O(n))  | No (O(n))         | No (O(n))   | Yes (O(1))        | Yes (O(n))  | Yes (O(n))                     |
| Insert            | Yes/O(n)   | No                | Yes (O(1))  | Yes (O(1))        | No (O(n))   | No (O(n))                      |
| Delete            | No (O(n))  | No                | Yes (O(1))  | Yes (O(1))        | No (O(n))   | No (O(n))                      |
| Memory Efficiency | Medium     | High              | Medium-High | Medium-High       | High        | Low                            |
| Best Use          | General    | Fixed data        | Fast lookup | Membership        | Numeric ops | Tabular data                   |
| Key Feature       |            | static; immutable |             | no inherent order |             | slow if iterating through rows |


## Code Formatting, Linting, and Type Checking
### Code formatting
- Python Enhancement Proposal 8 (PEP8)
- Import Formatting: PEP8 sets standards for how to group your imports - imports should be grouped in the following order
	1. Standard library imports
	2. Related third-party imports
	3. Local application/library specific imports
### Linting 
- Linting = checking your code for errors before it runs
- how to lint
	- use some tool packages
	- IDE automatically does this
### Type Checking
= check the type of the input that a function is expecting to avoid potential errors
- use type annotations
- use some tool packages

## Testing Code
### Basic test structure (from Pytest documentation)
1. arrange: set up everything needed to run the function
2. act: run the function
3. assert: check if the result is as expected
4. cleanup: cleanup the testing trace
### Types of Tests
- **[[Notes/Unit Tests\|Unit Tests]]**: check that units of code, such as functions or classes, do what a developer expects
- **Integration tests**: check that a larger system is connected correctly
- **Acceptance tests**: check that the system does what the user expects
- **Load tests**: check that the system still functions correctly if the amount of data or the number of users increases
- **Security tests**: check that the system is resistant to attacks
- **Usability tests**: check that the system is intuitive to use

### Testing for DS & ML
- data validation
- test model training & inference

## Design & Refactoring
### Code Design 
- modular code: critical to good design
- Framework
	- function name
	- inputs
	- behavior
	- outputs
### ML project structure
- example:
```
├── README.md 
├── requirements.txt 
│ 
├── notebooks 
│ ├── explore_data.ipynb 
│ └── try_regression_model.ipynb 
│ 
├── src 
│ ├── __init__.py 
│ ├── load_data.py 
│ ├── feature_engineering.py 
│ ├── model_training.py 
│ ├── model_analysis.py 
│ └── utils.py 
| 
├── tests 
│ ├── test_load_data.py 
│ ├── test_feature_engineering.py 
│ ├── test_model_training.py 
│ ├── test_model_analysis.py 
│ └── test_utils.py
```

### Refactoring
> *Refactoring is the process of changing a software system in a way that does not alter the external behavior of the code, yet improves its internal structure.* —Martin Fowler

## Documentation
- Names
	- Variables and functions should use snake_case
	- Class definitions should use CamelCase
	- Constants or global variables should use ALL_CAPS
- Comments
- Docstrings
- READMEs
- Experiment tracking

## Deployment
### Containers & Dockers
- container = an isolated place to run your API or any other application
- docker = a system for building and managing containers
### Cloud deployment
- common main steps
	1. create a Docker container on your local machine that contains the API code and details of the libraries
	2. upload this container to a container registry on a cloud profiler’s system (AWS, Microsoft Azure, or Google Cloud)
	3. deploy containers: instruct the cloud provider to run the chosen container
## Security
### What is security for software
- protecting a system from theft of information, damage, disruption, or unwanted access to information
### Commonly used terms
- **attacker**: Wants to steal data from or disrupt a software system
- **threat**: An event that has the potential to harm users of a software system or the company that runs the system
- **Vulnerability**: A weakness in a software system that could be exploited by an attacker
- **Risk**: The likelihood and severity of a threat being carried out
### Security risks & practices
- login credentials being stolen <- avoid committing secrets or data
- risk of third-party packages <- version control
- risk of pickle module (attackers could plant any code in a pickle file) <- use JSON instead 
- use static analysis tools to scan code without running it
- for production code: security reviews and policies
- specific security issues for ML (on deployed models or training data) <- validating training data, monitoring the model, and being able to rapidly deploy a new model if an issue is found

## Working in Software
### The Software Development Lifecycle
1. plan
2. design
3. build
4. test
5. deploy 
6. maintain
### Software development
- **Waterfall Software Development**: each step in the project lifecycle is carried out following the end of the previous one
- **Agile Software Development**: focuses on frequent updates to software
	- emphasize flexibility, rapid feedback from customers/users, and changing direction in response to events instead of making detailed plans for development
	- teams are often cross-functional
		- designers and analysts as well as developers
		- a product owner who represents the point of view of the users or customers
	- Agile methodologies: scrum, Kanban
### Technical roles in software inductry
- Software Engineers: Write code and develop processes to build and maintain products.
- QA Engineers: Test the product to check that it works well for all users.
- Data Engineers: Build and maintain data pipelines to transform raw data into a format that data scientists and analysts can use. 
- Data Analysts: Select, clean, analyze, and interpret data to derive insights from it. 
- Product Managers: Plan and organize the requirements and roadmap for development work. 
- UX Researchers: Research and analyze the needs of a product’s users. 
- UI/UX Designers: Design the overall look (UI) and feel (UX) of a product.