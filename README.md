# LINQ to SQL templates for T4

## Summary
T4 templates with the functionality of SQLMetal/LINQ to SQL classes designer code-generators for C# & VB.Net.

## Goal
Provide drop-in replacements that serve as a starting point for customized code generation. The templates also add:

- Can concurrency check when updating/deleting entities with stored procedures (switch on options.StoredProcedureConcurrency and have the SP return @@ROWCOUNT)
- Entity-per-file generation ability (does not rewrite unchanged files, cleans-up and checks out files that require changing automatically)
- DataContract serialization support for .NET 3.5 SP1 including KnownType & IsReference attributes
- Minor bug-fixes scheduled for inclusion in the .NET 4.0 release of SQLMetal/LINQ to SQL designer

## Getting started
Follow these simple steps:

1. Download the [latest release](https://github.com/damieng/L2ST4/releases) and extract the files
2. Drag the L2ST4.ttinclude and either CSharpDataClasses.tt or VBNetDataClasses.tt files to your project
3. Rename the .tt file to match your DBML file (retaining .tt instead of .dbml)
4. Turn off the existing .generated file beneath the DBML (set it's Build Action property to None)

Remember to use *Transform All Templates* or *Run Custom Tool* on the .tt file to run the template when the DBML has changed (it's not automatic).  If your .tt file does not have the *Custom Tool* property defined then set it to `TextTemplatingFileGenerator`.

## Limitations
Templates are a work-in-progress and you should ensure the generated code is suitable for your application. Limitations include:

- Reserved keyword checking not implemented
- String escaping not implemented (e.g. " or CRLF in table/column names)
- Tables with CRLF or " in the name break code generation
- Escaping a column or table name with [] but not the association reference causes lookup failure
