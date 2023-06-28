# Soliton C# Style Guide

Welcome to Soliton's C# coding conventions.

This contains the coding conventions/style guides for all C# code we develop.

## Coding Conventions

### Naming

- Names of solution, projects, namespaces, classes, properties, methods, enumerations: **PascalCase**.
- Names of local variables, parameters: **camelCase**.
- Names of private, protected, internal and protected internal fields: **_camelCase**.
- Name the variables intuitively by following similar patterns for similar data types/ files.
  - For example,
    - Boolean – Start with helping verbs.
      - **is**Checked, **can**Show, **do**SelfCalibrate.
    - List – Use the collective name with a suffix as ‘**List**’.
      - Employee**List**, Switches**List**.
    - Dictionary – Use Value **by** Key with a suffix as ‘**Dictionary**’.
      - EmployeeName**By**ID**Dictionary**.
    - Add suffix for any meaningful class types.
      - Use the suffix as '**Command**' for commands.
        - FileOpen**Command**.
    - Add the type of files as suffix to identify the C# files easily.
      - ViewModel – Employee**ViewModel**.
      - View – ProductsDisplay**View**.
      - Dialog – Login**Dialog**.
    - Add '**I**' as a prefix for all interfaces.
        - public interface **I**Employee
    - Use most common names for C# files with common purposes.
      - “**Constants.cs**” to store the constant values used across multiple c# files.
      - “**Utilities.cs**” / “**Reusables.cs**” to store the functions reused across multiple c# files.
    - Do not add additional prefix (or) suffix for child elements of a class.
      - If there is a property to store phone number of the employee in an 'Employee' class.
        - Name the property as just 'PhoneNumber' not as 'EmployeePhoneNumber' becuase ideally the property 'PhoneNumber' will be accessed using the Employee Object (EmployeeObject.PhoneNumber). So, having EmployeePhoneNumber will be redundant.
- Names for Acronyms and Abbreviation
    - Use either all uppercase or all lowercase for both letters if the acronym has only two letters.
        - string **id**; --> local variable
        - public string **ID** {get; set;} --> property
    - Use either all lowercase or PascalCase if the acronym has more than two letters.
        - **http**, **Http**
    - Do not use abbreviations which are not commonly accepted.
        - Use '**number**' instead of '**num**'
- Name the methods with verbs that indicates the action performed.
    - **Get**EmployeeStatus()
    - **Fetch**EmployeeDetails()
    - **Calculate**EmployeeSalary()

### Code Organinization

- The elements in class should be organized in following order,
    - Constant fields
    - Private fields
    - Constructor
    - Finalizers/Destructors
    - Delegates/Events/Enums
    - Public Properties
    - Public Methods
    - Internal Methods
    - Private Methods
    - Order by access – public, internal, protected internal, protected, private
