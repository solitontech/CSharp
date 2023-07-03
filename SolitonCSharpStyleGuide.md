# Soliton C# Style Guide

Welcome to Soliton's C# coding conventions V1.0.0.0.

This contains the coding conventions/style guides for all C# code we develop. This document is constantly evolving. New rules might be added over time.

## Coding Conventions

### Naming

- Identifiers must start with a ***letter*** or underscore (***_***).
    - Identifier is the name you assign to a type (class, interface, struct, record, delegate, or enum), member, variable, or namespace.
- Casing:
    - **P**ascal**C**ase: 
        - | Type | Example
          | ---- | ------- |
          | Solution, Projects | SolitonBank.sln , SolitonBankModel.cs |
          | Namespaces | namespace SolitonBank.Model {..} |
          | Class / Interface | public class Employee {..} |
          | Property, Event, Field | public int Name { get; }, public event MouseMoved |
          | Method | public double CalculateSalary() {..} |
          | Enum | public enum WorkMode { Office, Home } |
    - **c**amel**C**ase:
        - | Type | Example
          | ---- | ------- |
          | Local variables, Parameters | public static double CalculateSalary(string ***basicPay***) { double **grossSalary** = basicPay + HRA; ..} |
    - **_c**amel**C**ase:
        - | Type | Example
          | ---- | ------- |
          | Private, Protected, Internal and Protected internal fields | public class Employee { private double _houseRentAllowance  = 10000; .. }  |

- Choose the names more meaningful and follow similar patterns for similar data types/ files.
  - For example,
    - **Boolean** – Start with helping verbs.
      - **is**Checked, **can**Show, **do**SelfCalibrate.
    - **List** – Use collective name with a suffix as ‘**List**’.
      - Employee**List**, Switches**List**.
    - **Dictionary** – Use Value **by** Key with a suffix as ‘**Dictionary**’.
      - EmployeeName**By**ID**Dictionary**.
    - Add suffix for any meaningful class types.
      - Use the suffix as '**Command**' for commands.
        - FileOpen**Command**.
    - Add the type of files as suffix to identify the C# files easily.
      - ViewModel – Employee**ViewModel**.
      - View – ProductsDisplay**View**.
      - Dialog – Login**Dialog**.
    - Add '**I**' as a prefix for all interfaces.
        - public **interface** **I**Employee
    - Consider adding base class names as suffix for the derived class where it would be helpful for readability.
        - 'AccountNotFound***Exception***' which is a kind of Exception.
    - Consider using file name same as the name of the class in the file. In general, prefer one core class per file.
    - Namespaces can be named in the following format
        - ```<CompanyName>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]```
        - Example: Soliton.Bank.Model.Employee
        - Under a namespace, do not use same name for the classes as namespace's name.
            - Example: Use different names instead of Employee such as 'EmployeeData'.
        - Consider namespaces matches the folder hierarchy from source directory.
            - Example: the files in the folder hierarchy "C:\Repo\SolitonRepo\Bank\Model" may use the namespace as 'Soliton.Bank.Model.Employee'.
    - Use most common names for C# files with common purposes.
      - “**Constants.cs**” to store the constant values used across multiple c# files.
      - “**Utilities.cs**” / “**Reusables.cs**” to store the functions reused across multiple c# files.
    - Do not add additional prefix (or) suffix for child elements of a class.
      - If there is a property to store PhoneNumber of the employee in an 'Employee' class.
        - Name the property as just 'PhoneNumber' not as 'EmployeePhoneNumber' becuase ideally the property 'PhoneNumber' will be accessed using the Employee Object (EmployeeObject.PhoneNumber). So, having EmployeePhoneNumber will be redundant.
- Names for Acronyms and Abbreviation
    - Use either all uppercase or all lowercase for both letters if the acronym has only two letters.
        - string **id**; --> local variable
        - public string **ID** {get; set;} --> property
    - Use PascalCase if the acronym has more than two letters.
        - **Http**
    - Do not use abbreviations which are not commonly accepted.
        - Use 'number' instead of 'num'
- Special cases
    - When using product names in identifiers, match the trademarked product name. For example in an API that is exclusive to the shipping LabVIEW product, use "LabVIEW", not "LabView" or "labVIEW".
- Name the methods with verbs that indicates the action performed.
    - **Get**EmployeeStatus()
    - **Fetch**EmployeeDetails()
    - **Calculate**EmployeeSalary()

### Code Organinization

- The ```using``` statements should be outside of the namespaces in the file.
    - The using statements of system namespaces should be at the top followed by other namespaces.
    - Both the using statements of system and non-system namspaces should be alphabetically sorted.
    - Use alias for using statements that contains similar type names.
        - Example: If there is a class named as 'FileWrite' in Soliton.Bank.Model.Employee and Soliton.Bank.Model.Customer. Then alias can be used as follows,
            - `` using System;
            using Employee = Soliton.Bank.Model.Employee;
            using Customer = Soliton.Bank.Customer;
            namespace Soliton.Bank.FileOperations
            {
                public class BalanceSheet
                {
                    public void SaveBalanceSheet()
                    {
                        Employee.FileWrite.Save();
                        Customer.FileWrite.Save();
                    }
                }
            }
            ``
- Arrange the class elements in the following order,
    - Constant fields
    - Private fields
    - Constructor
    - Finalizers/Destructors
    - Delegates/Events/Enums
    - Public Properties
    - Public Methods
    - Internal Methods
    - Private Methods
    - Within each of the above elements group, Arrange in following order of access modifiers
        – public
        - internal
        - protected internal
        - protected
        - private


### Documentation
- Use XML documentations for class and its all elements inside.
    - In VisualStudio, type forward slash('/') three times as '***///***'. The xml documentation syntax will be added. Take time and fill in with the good documentation as it would be the starting point for anyone who reads the code first.
    - For complex logics and loops inside the methods, add neccessary documentation exaplaining the need of the logic and how it works using double forward slash ('***//***')
    - Documentation cannot be added for Namespaces.
- Do not have any commented code while pushing to repo.
- Refer the [link](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/) for XML documentation tags's usage and examples. 


### Language Features

- Remove unused imports.

- Use primitive C# types instead of Framework Class Library (FCL) types.
    - Primitive Types
        - sbyte, byte, short, ushort, int, uint, long, ulong, char,
float, double, bool, decimal, object, string.
    - Framework Class Library (FCL) Types
        - SByte, Byte, Int16, UInt16, Int32, UInt32, Int64, UInt64, Char,
Single, Double, Boolean, Decimal, Object, String

- Use either private fields (or) public properties. Do not use public fields.

- String
    - Use ***StringBuilder*** over string and operator '+' for multiple string concatenations as it will be faster.
- Const | ReadOnly
    - Declare the property as const if it's value is not going to be changed in the run time.
    - Prefer using const if it's value is going to be changed in the run time.
- ref and out
    - Use ***out*** for return parameters that are not also an input.
    - Place ***out*** parameters after all other parameters in the method definition.    


### General Guidelines
- Fix the errors and warnings reported by analyzers.
- Keep the method as simple as possible.
- Reuse code. Do not repeat anything which have already implemented.

