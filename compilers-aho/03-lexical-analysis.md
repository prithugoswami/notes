---
geometry:
- lmargin=0.9in
- rmargin=0.3in
- tmargin=0.3in
- bmargin=0.5in
- twoside
papersize: A4
...

\begin{huge}
\textbf{Chapter 3 - Lexical Analysis}
\end{huge}


We usually use *lexical-analyser generators* to which we feed the patterns of
the lexemes and the generator then produces code that works as a lexical
analyser. These patterns are specified using regular expressions. These
expressions are converted into NDFSM and then to DFSM. These two models are
then fed to a "driver" that simulates these automaton and decide the next
token.

# The Role of the Lexical Analyzer

- Main task - read the input characters of the source program, group them into
  lexemes and produces as output a sequence of tokens for each lexeme in the
  source program. The stream of tokens is then sent to the parser for syntax
  analysis
- It also interacts with the symbol table.
- The interactions between the parser and the lexical analyser are depicted in
  the Fig 1 and it's implemented in a way where the parser calls the lexical
  analyser by the *getNextToken* command. The calls causes the lexical analyser
  to read characters from the input and determine the next lexeme and produce
  the next token for the parser.

![Interaction between Lexical Analyser and parser](img/interaction-parser-lex.png){width=70%}

- Lexical analyser may also perform some other tasks like stripping out
  whitespaces and comments.
- It may also indicate errors by inserting error message in the appropriate
  lines by keeping track of line numbers and may also perform macro expansion.
- Sometimes they are divided into **two processes**:
  1. **Scanning** consists of simple process that do not require tokenization
  like deleting comments and whitespaces.
  2. **Lexical Analysis** is the main part where the scanner produces output as
  a sequence of tokens.

## Lexical Analysis Versus Parsing.

Reasons why the analysis process of compiler is split into lexical analyser and
parser (syntax analyser):

1. **Simplicity of design**. The separation of tasks helps us simplify at
   leasts one of those tasks. Like the lexical analyser once done with dealing
   with whitespaces and comments, it's easier and simpler for the syntax
   analyser to parse it with the assumption that the comments and the
   whitespaces have been removed rather than having to process them as well.
2. **Compiler efficient is improved.** A separate lexical analyzer helps us to
   apply specialized techniques to improve the efficiency only of the lexical
   task. Like one example is using specialized buffering techniques during
   reading the input to speed up the compiler.
3. **Portability is enhanced**. Input-device-specific peculiarities can be
   restricted to lexical analyzer.

## Tokens, Patterns, and Lexemes

- A **token** is a pair consisting of a token name and a token attribute value.
  The token name is an abstract symbol representing the kind of lexical unit,
  e.g., a keyword, or an identifier.
- A **pattern** is a description of the form the lexemes of a token may take.
  In the case of a keyword as a token, the pattern is just a sequence of
  characters that form that keyword.
- A **lexeme** is a sequence of characters that matches the pattern for a token
  and is identified by the lexical analyzer as an *instance* of that token.

## Attributes for tokens

- Attribute values for tokens are used to provide more information about the
  token. For example a token of number matches both the lexemes `0` and `1`,
  thus to provide more information to the other phases of the compiler,
  attribute values are used.
- The token name influences how the parsing is done, while the attribute value
  influences the translation of the tokens after the parse.
