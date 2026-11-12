# Doxygen –Code Documentation

## 1. Introduction to Documentation

Technical documentation explains how a software system works, what its components do, and how they should be used.

Documentation plays an important role in software development because it:

- Clarifies requirements and specifications.
- Makes software maintenance easier.
- Helps new developers understand an existing codebase.
- Supports compliance, auditing, and quality control.
- Encourages knowledge sharing and collaboration.

## 2. What is Doxygen?

**Doxygen** is an open-source documentation generator used to automatically create software documentation from specially formatted comments in source code.

It supports several programming languages, including:

- C
- C++
- Python
- Java

Doxygen extracts information from documentation comments and generates reference manuals in formats such as HTML, LaTeX/PDF, RTF, XML, DocBook, and man pages.

It is widely used for documenting software libraries and APIs.

### Key Features

- Extracts documentation for functions, classes, and modules.
- Generates cross-referenced documentation.
- Supports call graphs and inheritance diagrams.
- Supports Markdown and LaTeX mathematical expressions.
- Allows diagrams using Graphviz and other supported tools.
- Can be integrated into CI/CD workflows.

## 3. Installing Doxygen

Doxygen can be installed on different operating systems.

| Operating System | Installation |
|---|---|
| Windows | Download the installer from the official website. |
| macOS | `brew install doxygen` |
| Linux (Debian/Ubuntu) | `sudo apt-get install doxygen` |

Official website: https://www.doxygen.nl/download.html

### Verify Installation

After installation, open a terminal and execute:

```bash
doxygen --version
```

This displays the installed Doxygen version.

## 4. Basic Doxygen Workflow

The documentation-generation process follows four major steps:

1. Write specially formatted comments in the source code.
2. Generate or edit the Doxygen configuration file.
3. Run Doxygen using the configuration file.
4. Browse the generated documentation.

### Step 1: Generate Configuration File

```bash
doxygen -g Doxyfile
```

This generates a default configuration file named `Doxyfile`.

### Step 2: Configure Documentation

The Doxyfile contains settings that control documentation generation.

Some important settings include:

```ini
PROJECT_NAME = "My Project"
OUTPUT_DIRECTORY = docs
INPUT = .
RECURSIVE = YES

GENERATE_HTML = YES
GENERATE_LATEX = YES
```

### Step 3: Generate Documentation

```bash
doxygen Doxyfile
```

This command generates documentation according to the configuration.

### Step 4: View the Output

For HTML documentation, open:

```text
docs/html/index.html
```

The generated website contains documented functions, classes, references, and other project information.

## 5. Doxygen Comment Syntax

Doxygen recognizes specially formatted comments and extracts their descriptions.

### C/C++ Documentation Comments

One commonly used format is:

```cpp
/**
 * @brief Brief description of the function.
 *
 * Detailed explanation of the function.
 * @param x Description of the parameter.
 * @return Description of the return value.
 */
int myFunction(int x);
```

Another supported format uses three forward slashes:

```cpp
/// @brief Calculates the square of a number.
/// @param x Input number.
/// @return Square of the number.
int square(int x);
```

The special comment syntax allows Doxygen to distinguish documentation from ordinary source-code comments.

### Python Documentation

Doxygen can also extract documentation from Python docstrings.

```python
def foo(bar):
    """
    Brief description.

    More details here.

    :param bar: Bar parameter
    :type bar: int
    :return: Computed value
    :rtype: int
    """
    return bar + 1
```

This example demonstrates parameter and return-value documentation using a Python docstring.

## 6. Common Doxygen Tags

Doxygen provides special commands, also called tags, to organize documentation.

| Tag | Purpose |
|---|---|
| `@brief` or `\brief` | Short description of a function, class, or module. |
| `@param` or `\param` | Describes a function parameter. |
| `@return` or `\return` | Describes the returned value. |
| `@author` or `\author` | Specifies the author. |
| `@version` or `\version` | Specifies the version. |
| `@see` or `\see` | Refers to related documentation. |
| `@note` or `\note` | Adds an additional note. |

### Example

```cpp
/**
 * @brief Adds two integers.
 *
 * Calculates the sum of two numbers.
 *
 * @param a First integer.
 * @param b Second integer.
 * @return Sum of the two integers.
 * @author Student
 * @version 1.0
 */
int add(int a, int b) {
    return a + b;
}
```

The generated documentation will contain the function's description, parameters, return value, author, and version.

## 7. Documenting Classes

Doxygen can generate documentation for classes and their member functions.

```cpp
/**
 * @class Car
 * @brief Represents a car object.
 *
 * This class provides basic car operations.
 */
class Car {
public:

    /**
     * @brief Starts the engine.
     * @return True if the engine starts successfully.
     */
    bool startEngine();
};
```

Here:

- `@class` identifies the class being documented.
- `@brief` provides a short description.
- The member function has its own documentation block.
- `@return` explains the function's return value.

Documenting classes makes it easier for developers to understand the responsibilities and functionality of different components.

## 8. Grouping and Diagrams

Doxygen supports advanced documentation features that help organize large software projects.

### Grouping

Related functions, classes, or modules can be grouped together using Doxygen grouping commands.

Example:

```cpp
/**
 * @defgroup MathFunctions Mathematical Functions
 * @{
 */

/** @brief Adds two numbers. */
int add(int a, int b);

/** @brief Subtracts two numbers. */
int subtract(int a, int b);

/** @} */
```

The `@defgroup` command defines a group, while `@{` and `@}` mark its beginning and end.

### Graphs and Diagrams

Doxygen can generate several diagrams, including:

- Call graphs.
- Include dependency diagrams.
- Inheritance diagrams.

Graphviz can be used to generate these diagrams.

An important configuration option is:

```ini
HAVE_DOT = YES
```

Graphviz must also be installed and accessible for the corresponding diagrams to be generated.

Doxygen additionally supports embedded diagrams using `@dot` and PlantUML directives.

## 9. Doxygen Output Formats

Doxygen can generate documentation in multiple formats.

| Format | Purpose |
|---|---|
| HTML | Interactive documentation for web browsing. |
| LaTeX/PDF | Printable technical manuals. |
| RTF | Rich Text Format documents. |
| XML | Structured documentation data. |
| DocBook | Documentation in DocBook format. |
| Man Pages | Unix manual pages. |

### Configuration Example

```ini
GENERATE_HTML = YES
GENERATE_LATEX = YES
GENERATE_RTF = NO
GENERATE_XML = NO
```

These options control which output formats are generated.

HTML is enabled by default and is particularly useful for browsing project documentation.

## 10. Best Practices for Writing Doxygen Documentation

Good documentation should explain not only what a function does but also its purpose and expected behavior.

Recommended practices include:

1. Describe the purpose and contract of functions.
2. Keep brief and detailed descriptions separate.
3. Document public APIs and modules.
4. Use a consistent set of documentation tags.
5. Keep documentation updated whenever the source code changes.
6. Include documentation generation in continuous integration workflows.

## 11. Doxygen with Version Control

Doxygen can be integrated with Git and GitHub to maintain documentation alongside source code.

Recommended practices include:

- Store the `Doxyfile` in the source repository.
- Update documentation whenever code is modified.
- Review documentation changes through code reviews.
- Publish generated documentation using GitHub Pages or an internal documentation platform.

Keeping documentation and source code together helps ensure that documentation remains consistent with the implementation.

## 12. Practical Exercise: Doxygen Mini-Project

The lecture proposes the following hands-on exercise:

1. Download and install Doxygen.
2. Select a small C++ or Python codebase.
3. Add specially formatted documentation comments using Doxygen tags.
4. Generate HTML documentation.
5. Open `html/index.html` in a browser.
6. Explore generated diagrams and cross-references.

### Expected Outcome

After completing this exercise, a developer should be able to understand how source-code comments can be converted into structured software documentation.

## 13. Learning Outcomes

After studying Doxygen, the following concepts can be understood:

- Importance of technical documentation in software development.
- Working principles of an automated documentation generator.
- Installation and configuration of Doxygen.
- Writing documentation comments in C++ and Python.
- Using common Doxygen tags.
- Documenting functions and classes.
- Generating diagrams and cross-referenced documentation.
- Producing HTML and other documentation formats.
- Integrating documentation into version-control workflows.

## 14. Conclusion

Doxygen simplifies software documentation by automatically extracting information from specially formatted source-code comments.

It helps developers create structured, maintainable, and easily accessible reference manuals. By integrating Doxygen with version control and development workflows, software teams can keep documentation closely connected to their source code.

## 15. References

- [Official Doxygen Website](https://www.doxygen.nl/)
- [Doxygen Manual](https://www.doxygen.nl/manual/)
- Lecture: *Introduction to Documentation Tools: Doxygen & Google Docs*, Dr. Neeta Nain, MNIT Jaipur, September 11, 2025.

---
