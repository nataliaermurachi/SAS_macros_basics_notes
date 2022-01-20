## SAS_macros_basics_notes
> *SAS Macro* - can reduce the development and maintenance time;
* you can modify the repeating values in your code by using macro variables
* those values are automatically substituted into SAS program each time it executes
* no need to manually update the code

### *Six step process to develop macro application:*

1. Start with a validated SAS program
2. Generalize with macro variables
3. Create a macro definition with parameters 
4. Use macro-level programming for complex processing
5. Add data-driven features
6. Validate parameters and document

### *Sas Programming Languages:*

* DATA step language -> data manipulation
* SQL procedure -> data manipulation and reporting
* SAS procedures -> data analysis and reporting
* SAS macro language -> generate SAS program code

### *Porgram flow in program that includes macro code:*
* Sas code is sent to the compiler
* Macro code is sent to the macro procesor

**SAS program** --> **Input Stack** - (*an area of memory where code is sent after submiting the code*) --> **Word Scanner** - (*a SAS component that pulls the row text from the input stack l->r t->b - **tokenization***) --> **Compiler** and --> **Macro processor**

> *A token* - the original text with an attached metadata tag to help SAS process it.
* Whitespace characters separate tokens
* A token ends when a new type of token begins

### *Type of tokens:*
* **name tokens** 
    * must begin with letter or _, up to 32 characters
    * followedby letters, underscores and digits
    * includes keywords, filenames, column names
* **Number tokens** 
    * include digits, a decimal point, a leading sign and an exponent
    * also includes SAS date, time, and datatime constants
* **Literal tokens**
    * character strings enclosed in "" or ''
    * max length 32767 bytes
* **Special tokens**
    * any character that is not a letter, number or underscore
    * *, #, >, /, % ...

***A macro trigger***:
* & - macro variable
* % - macro statement, macro function, macro call

`%PUT [PREFIX] text;` - macro statement that writes text to the log:

Use **NOTE**, **WARNING**, **ERROR** prefixes  to color the log message

> The compiler is not involved in processing macro code

> Macro variables are stored in a memory-based symbol table
> All macro variable values are stored as text

> Mathematical expressions are not evaluated

> When the SAS session ends, the global symbol table is deleted

Macro variable names:

    *Follow SAS naming rules*
    *are stored as uppercase*
    *are not case sensitive*

Macro variable values:

    *Case is preserved*
    *Leading and trailing blanks are removed*
    *Store 0 to 65534 characters*
    *The length is dinamically set each time a value is assigned*

`%SYMDEL list of variable names;` 
* explicitly deletes variables from the global symbol table
* accepts a list of macro variable names
* releases memory back to the system

Declare a variable: `%LET name=value;`

Access its value: `&macro-variable-name`
