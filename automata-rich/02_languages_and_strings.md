---
geometry:
- lmargin=0.9in
- rmargin=0.175in
- tmargin=0.3in
- bmargin=0.5in
- twoside
papersize: a4
classoption:
- twocolumn
...

## Strings
### Definitions
- **Alphabet ($\Sigma$)**\
    A a **finite set** consiting of symbols or characters.
- **String**\
    A **sequence** of symbols drawn from some alphabet $\Sigma$. A string can
    be empty, denoted by $\epsilon$
- **$\boldsymbol\Sigma$\***\
    Denotes the set of **all possible strings** over an alphabet $\Sigma$$\*$

### Functions on a string
- **length**\
    $|\epsilon|=0$\
    $|100111|=6$
- **character occurences**\
    $\#_a$(`abbaa`) = 3
- **concatenation**\
    $x = good$, $y = bye$\
    $xy=goodbye$, $yx=byegood$\
    Also, $x||y\ = goodbye$ (Another notation)\
    \- The empty string $\epsilon$ is the identity of the concatenation.
    $$\forall x(x\epsilon = \epsilon x = x)$$
    \- Concatentation is also associative. $$\forall s,t,w\ ((st)w = s(tw))$$
- **replication**\
    $$w^0 = \epsilon$$ $$w^i = w^{i-1} w$$
    $a^3 = aaa$ , $(bye)^2 = byebye$ , $a^0b^3 = bbb$
- **reversal**\
    For a string $w$, the reversal $w^R$ is defined as:
    \begin{equation}\notag
        \text{if }|w| = 0 \text{ then } w^R = w = \epsilon
        \\[-0.3in]
    \end{equation}

    \begin{equation}\notag
    \begin{split}
        &\text{if }|w| \geq 1 \text{ then } \exists a \in \Sigma(\exists u \in
        \Sigma^\ast (w = ua))\\
        &\text{then } w^R = au^R
    \end{split}
    \end{equation}

### Theorem 2.1
If $w$ and $x$ are strings, then $(wx)^R=x^Rw^r$

### Relations on Strings
- **substring**\
    A string $s$ is a substring of a string $t$ iff $s$ occurs contiguously as
    a part of $t$\
    A string $s$ is a **proper substring** of a string $t$ iff $s$ is a 
    substring of $t$ and $\bold{s \neq t}$
- **prefix**\
    A string *s* is a prefix of *t* iff $\exists x \in \Sigma^\ast(t = sx)$\
    **proper prefix** again same as above ($\bold{s \neq t}$)
- **suffix**\
    A string *s* is a suffix of *t* iff $\exists x \in \Sigma^\ast(t = xs)$\
    **proper suffix** again same as above ($\bold{s \neq t}$)

**Empty string $\epsilon$ is a suffix, prefix and a substring of every string**

## Languages

A **language** is a **finite or infinite set of strings** over a fine alphabet
$\Sigma$.\
For a language *L* defined over alphabet $\Sigma$,  $L\subset \Sigma^\ast$\
$\Sigma_L$ is used to denote the alphabet from which the strings in the 
language *L* are formed.

### Ways of defining languages
- We can have a **language generator** that **enumerates** the elements of the
language or have **language recognizer** which **decides** whether or not a 
candidate string is in the language and returns *True* if it is and *False*
if it isn't.

- **Go through examples on page 11-13 to see different ways languages
are defined**
- Empty language $L = \{\}$ = $\varnothing$ is a language that contains no
strings but a language $L = \{\epsilon\}$ is not an empty language as it
consists of one element i.e., an empty string.
- **Lexigographic order**
    - Sometimes we may care about the order in which the elements of a
    language are generated in.
    - If there exists a total order *D* then we can use *D* to define on *L*
    a useful total order called **lexicographic order** (written $<_L$):
    $$ \forall x(\forall y((\ |x| < |y|\ )\to (x <_L y)))$$
    and of the strings of the same length, sort them in dictionary order using
    *D*.

### Cardinality of a language
- The smallest language over any alphabet is $\varnothing$ with cardinality of 0
- The largest language over any alphabet $\Sigma$ is $\Sigma^\ast$
- For $\Sigma = \varnothing,\ \Sigma^\ast = \{\epsilon\}$ and $|\Sigma^\ast|=1$
  theorem 2.2 is for non-empty alphabets.

### Theorem 2.2
If $\Sigma \neq \varnothing$ then $\Sigma^\ast$ is countably infinite
($\aleph_0$)
- Therefore, the cardinality of every language is at least 0 and at most
${\aleph_0}$

### How many languages are there?
- The set of languages defined on $\Sigma$ is $P(\Sigma^\ast)$
- For $\Sigma = \varnothing,\ \Sigma^\ast = \{\epsilon\}$ and $P(\Sigma^\ast)\ 
is\ \{\varnothing, {\epsilon}\}$
- But when $\Sigma \neq \varnothing$ theorem 2.3 applies.

### Theorem 2.3
If $\Sigma \neq \varnothing$ then the set of languages over $\Sigma$ is
uncountably infinite.

### Functions on a language
- Since languages are sets, all of the standard set operations are well-defined
on languages. (refer Ex2.12 from page 15)
- **concatenation**\
Let $L_1$ and $L_2$ be two languages defined over $\Sigma$ then:
$$L_1L_2=\{w\in \Sigma^\ast : \exists s \in L_1(\exists t \in \L_2(w = st))\}$$\
Example\
Let $L_1 = \{\texttt{cat, dog, mouse}\}$ and $L_2 = \{\texttt{bone, food}\}$\
\vspace{-0.2in}
\begin{multline}\notag
L_1L_2 = \{\texttt{catbone, catfood, dogbone, dogfood,}\\
\texttt{mousebone, mousefood}\}
\end{multline}
\- The language {$\epsilon$} is the identity for concatenation of languages.
For all languages *L*:
$$L\{\epsilon\} = \{\epsilon\}L = L$$
\- The language $\varnothing$ is a zero for concatenation of languages.
For all languages *L*:
$$L\varnothing = \varnothing L = \varnothing$$
There are no ways of selecting a string from an empty set.\
\- It's also associative
$$(L_1L_2) L_3 = L_1(L_2L_3)$$
- **Kleene star**\
Let *L* be a language defined over $\Sigma$ then:
\begin{multline}\notag
    L^\ast = \{\epsilon\} \cup \{w \in \Sigma^\ast : \exists k \geq 1
    (\exists w_1, w_2,\dots w_k \in L\\
    (w = w_1w_2\dots w_k))\}
\end{multline}
note[^1]\
Example:\
\begin{equation}\notag
\begin{split}
    \text{Let }L  = & \{\texttt{dog, cat, fish}\}\text{. Then:}\\
          L^\ast  = & \{\epsilon\texttt{, dog, cat, fish, dogdog, dogcat,\dots,}\\
          & \texttt{fishdog, fishcat, fishfish,\dots,}\\
          & \texttt{fishcatfish,fishdogfishcat,\dots}
          \}\\[0.1in]
\end{split}
\end{equation}
\- $L^\ast$ always contains an **infinite number** of strings as long as *L*
is not $\varnothing$ or {$\epsilon$}. i.e., as long as there is one nonempty
string in *L*.\
\- If *L* = $\varnothing$, then $L^\ast$ = {$\epsilon$} as there are no strings
that could be concatenated to $\epsilon$ to make it longer. This means that
the Kleene star of any language must have at least $\epsilon$ in it.\
\- If $L=\{\epsilon\}$, then $L = \{\epsilon\}$ as well.

[^1]: The part $\exists w_1, w_2,\dots w_k \in L$ should mean 'select *k*
elements from *L*'. Each time selecting *k* elements in a particular
permutation and concatenating them.

- **reverse**
Reverse of a language *L* defined over $\Sigma$, written as $L^R$ is:
$$L^R = \{w \in \Sigma^\ast : w = x^R \text{ for some }x \in L \}$$


### Theorem 2.4
If $L_1$ and $L_2$ are languages, then $(L_1L_2)^R = L_2^RL_1^R$

### Assigning Meaning to Languages

To be able to use the language and form the framework for it's applications
we need to assigning meaning to its strings. Working with formal languages
require a precise way to assign meaning to strings (also called its
**semantics**).
\- A function that maps strings to its meanings is called a **semantic
interpreation function**. But since languages are infinite, its not, in general
possible to map each string with its meaning.\
\- Instead we define a function in such a way that it identifies units and can
combine those units based on rules to build meanings for larger expression. We
call such a function, **compositional semantic interpretation function**\
\- So this function "composes" the meanings of simpler constituents into a
single meaning for a larger expression.\
\- When we define a formal function to fulfill a specific purpose, we design
it so that there exists a compositional semantic interpretation function.\
\- For example there exists a compositional semantic interpretation function
for the C programming language, a C compiler.\
\- These functions are generally *not* one-to-one. For example:\
\vspace{-0.2in}

- "Chocolate, please", "I'd like chocolate", "I'll have chocolate" all mean the
same
- These also have to same meaning
  ```
  int x = 4;    int x = 4;     int x = 4;
  x++;          x = x --1;     x = x + 1;
  ```
