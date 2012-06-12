Developer Tools Kickoff
==========

@object literals
-----

@"" - strings

@# - numbers
    ex: ```@42``` or ```@(40+2)```
    
@{} - dictionaries
    ex: ```NSDictionary *dictionary = @{ @"Key", @"Value" };```
@[] arrays
    ex: ```NSArray *array = @[@"Things", @"Other Things"];```


XCode Enhancements!
-----

* Prioritizes code completion results!
* Refactor > Convert to Modern Syntax
* Search & Replace using regex or *simple pattern searches*, to insert a token that matches any pattern of characters (semi-colons, line breaks, etc)
* Don't have to forward-declare methods only used in the implementation/private methods
* **Callers Assitant Category** : Shows where the method you have selected is called from

*Editor Improvements*

* **Improved quick help** - just press ```option``` key when API method is selected 
* **Trailing whitespace removal!**
* **Replace in Selection** - hold option key to replace in selection instead of replace all
* **Symbolic Searches** - definitions, references of symbols throughout project
* **Caller/Callee Assistant Editor**
* **Selective Commit** - comparision view has new control to "Don't Commit" to allow for cherry-picking changes
* **Source Control Branching** - creates new branch and commit!

*Design*

* 