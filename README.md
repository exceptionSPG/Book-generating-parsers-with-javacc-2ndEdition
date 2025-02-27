# Generating Parsers with JavaCC book examples/tutoris


Compile:
javacc file.jj

run:
java ranged-characters/RangedCharParser.java "h"

## Structure of a javacc file
Javacc file has 4 parts:
1. Optional **_options_** section
2. Parser class definition
3. Lexical specification
4. Syntactic specification

### 1. Options
JavaCC has many built-in options to use while compilation. We can pass these options directly from commandline too. We have used following options so far:
a. BUILD_PARSER: true; --> This is to tell javacc compiler we want to build the parser, not just other files.
b. OUTPUT_DIRECTORY: "./path-to-parser-directory"; --> This allows us to compile/build our parser in a path specified.



## Files and their details:
### Chapter 1: Introduction
In this chapter, we gained brief overview on what we can do with javacc. Here, we created some files:
1. parse_a.jj --> this parses character "a", throws error else.
   Run by: `java ../../ch1_introduction/parse_a_cc/ParseA.java`

2. parse_atoz.jj --> this parses any single characters from a to z.
   Run parser by: `java ../../ch1_introduction/parse_atoz_cc/ParseAtoZ.java "b"`

Further, we learned about ant, and maven build tool.

### Chapter 2: Tokenizing
Here, we learned many aspects of tokenizing process. Some sub-topics, and files created are:

1. hello.jj
    Here, we didn't build the parser itself, rather we build tokenizer files and other essential files that javacc generates for us.
    Then, we created a runner file, and utilized those tokenizer files to parse the text "hello"
   Run hello parser by: `java ../ch1_tokenizing/hello_cc/HelloRunner.java`

2. reg_expressions
   In this, we learned many types of regular expressions and tried to implement them using javacc.
   1. literals.jj
   2. characters.jj
   3. ranged_characters.jj
   4. ranged_characters_alternation.jj
   5. mixing_character_and_ranged_characters.jj
   6. negation.jj
   7. negation_range.jj
   8. repetition.jj
   9. repetition_range.jj
   10. quantifier_oneormore.jj (+ quantifier)
   11. quantifier_zeroorone.jj (? quantifier)
   12. quantifier_zeroormore.jj (* quantifier)
   

3. Definining multiple tokens
   We can use alternation operator (|) to define multiple tokens. 
   However, concern arises if there is more than one possible match. In such case, two rules applies. 
   1. **Maximul munch rule** <br> This rule states JavaCC will consume the token that matches the largest amount of input data.
      1. longest_match.jj
      Here, we omitted main part inside parser class, but used  `TOKEN_MGR_DECLS` and build_parser to true (opposed to book, as keeping this false doesn't generate TokenManager file).
      After that, run as `java longest-match/LongestMatchTokenManager.java "hello"`
      
   2. **First select rule**
4. Redundant tokens
   Here, we learned about importance of ordering of tokens. 
   1. never_match.jj 
   2. first_match.jj

5. Private Token definitions
   private_regex.jj
   
6. SKIP regular expression production
   Helps us skip some unwanted characters/tokens. Helpful in skipping comments, spaces, etc.
   1. literals_space_token.jj 
   2. literals_space_skip_named.jj 
   3. space_skip.jj 
   4. skip_greedy.jj 
   5. Skipping_Uppercase.jj
   

7. Single Line comments
   We define skip rule for a line starting with ^^
   1. single_line_comment.jj
   run by: `java single-line-comment/SingleLineCommentTokenManager.java "hello hello ^^ this is comment and will be skipped.\n hello"`


8. MORE regular expression production
   Used when we don't want to discard certain block of data but don't want to do anything with them either:
   1. more_name.jj
9. SPECIAL_TOKEN regular expression
10. f
11. 
9. 
9. 
