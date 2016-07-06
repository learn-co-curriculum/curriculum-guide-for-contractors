# English Style Guidelines:

This section is a collection of English and Markdown writing notes. It includes syntax choices to improve clarity, corrections to common misuses, and tricks about rendering style in [Github-flavored markdown](https://help.github.com/categories/writing-on-github/).
 
## `##` Section headers

### `###` Sub-section headers.

#### `####` Sub-sub-section headers. 

##### `#####` Example Headers (optional).

###### `######` unused grey example header.


Section headers are valuable for linking to specific spot in a readme or lesson. The URL can be grabbed by clicking on the `∞` ("link") button that shows itself to the left of a section header. This link can be passed to a student when answering a question.

### Code Snippets

Do **not** include English punctuation in code snippets.

#### Code Blocks

```objc
NSString *code = @"Code ";
NSString *block = @"block.";
NSString *codeBlock = [code stringByAppendingString:block];
```

"Code blocks" are declared by wrapping in triple back-ticks ( ``` ). The opening triple back-tick should be followed with a language declaration appropriate to the contents of the code block:

`bash` : Bash, CLI output  
`ruby` : Ruby  
`objc` : Objective-C  
`swift`: Swift 
(none) : LLDB console output

The example code block above is written in markdown with the following syntax:

\`\`\`objc  
NSString *code = @"Code ";  
NSString *block = @"block.";  
NSString *codeBlock = [code stringByAppendingString:block];  
\`\`\`

#### Code Words

When discussing a "code word" as part of a regular sentence, wrap the code word in single back ticks ( \` ). This could be a variable name (`myString`), a class name (`NSArray`), a method name (`.include?`), an operator (`<=>`), or a string literal (`"Hi, Grandma."`); in general, any piece of code that does not constitute a whole line or statement.

Avoid beginning a new paragraph with a code word:

Not: `pwd` means "print working directory".  
Use: The `pwd` command means "print working directory".  

Also avoid beginning a new sentence with a code word whenever possible, though a semicolon `;` can be employed if altering the english syntax would make the paragraph awkward.

##### Symbols

Put a symbol into a `code snippet` when discussing it in a paragraph. On its first occurrence in a reading, follow the symbol with a lexicon/pronunciation guide in double quotes inside a parenthetical, e.g. `:` ("colon") or `*` ("star").

#### Code Phrases

A "code phrase" is a code snippet that contains more than one word but does not constitute a whole line (`NSString *hello`) or in its entirety is a short statement `hello = "hello world"` being discussed as the subject or direct object in a sentence. Code blocks can interrupt the flow of the writing, so a code phrase should only merit its own code block if it's too long to naturally fit into a sentence.

### Capitalization

Names of languages should be capitalized unless part of a code snippet (e.g. Ruby or `ruby`, Objective-C, Python or `python`; not: ruby, objective-c, python).  
Capitalize as proper nouns the names of software tools (e.g. Xcode, Learn.co (proper noun), RSpec vs. xcode, learn (verb form), rspec).

Don't capitalize:

* autolayout (iOS)
* bash — the commonly-used acronym for Bourne-Again SHell.
* boolean — though in specific reference to the fields of Boolean Algebra or Boolean Logic this can be appropriate, just be consistent.
* debug console (iOS) — this is a colloquial name for the 'Console Output Viewer' in Xcode

**Do** capitalize:

* *most acronyms:* CLI, URL, HTTP, LLDB.
* *names of programming languages:* Python, Ruby, Objective-C, Swift
* Interface Builder — Xcode's integrated storyboard design tool.


### Asides

**Note:** *The basic aside for "whispering" something minor that doesn't fit into the flow of exposition.*  
**Advanced:** *A helpful note that is not readily understandable to the present skill level of the reading and not required to fulfill the objectives.*  
**Top-tip:** *A note about style or best-practice, or a friendly reminder about avoiding a common or simple mistake. Think opinion-piece.*  
**Hint:** (in labs) *A note about avoiding a common mistake not readily apparent in the given instructions, or direction to a useful method that has not been previously explained.*  
**//Flat-fact:** *Read "fun-fact". Helpful for inserting informational tidbits relevant to the context of a reading without breaking the flow of instruction.*  
**Reminder:** *A reminder of previously learned concepts as we start to build on them.* 

**Custom:** *If none of these fit, write something yourself, such as* "**A Note To Fellow Tolkien Nerds:**".  

### Long Dash (Em-Dash) Literal

Employ the the long dash character `—` directly by pressing `shift``option``-` instead of a double short-dash (`--`). This will also avoid the possibility of rendering the dash as a bulleted list.

### Soft Return

Ending a line with `space``space``enter`  
will be displayed as a soft return  
without paragraph spacing.

### Quoting

Hyperlinks are the best way to note attributions.

##### Literary Quote

*You can use soft returns to manually enter  
a short quote in italics, such as a lyric.*  
—*attribution* and author.

These best belong immediately after a section or sub-section header and not within a body of exposition. They should be used sparingly, as for lyrics, axioms, poems, or lines from a work of literature which is not a technical part of the discussion, but rather more philosophical or otherwise enriching.

##### Block Quote

>You can employ an html-style block quote by starting the first line with an `>`. This is better for large excerpts when line breaks don't matter. (attribution or link)

More commonly a block quote will be appropriate when quoting a technical work, programming documents, or a blog.

##### In-Line Quote

When writing an "in-line quote", punctuation should remain outside the phrase "unless you are making a reference quote that includes it." Punctuation symbols can have technical importance to the subject matter so explicitly excluding punctuation from quotes is justifiable.

### Lists:

1. Lists can be automatically numbered,
   * and contain bullet points.

* Or they can be unnumbered (bulleted) lists.

2 — You can also manually number your list if the automatic numbering gets broken because of a code-snippet.

But, keep a consistent style. And generally avoiding making a list with only one point. Consider using an aside

### Numerology

When discussing number in exposition paragraphs, remember the English rule that numbers ten and below should be written out, and values over 1,000 should be written with comma separators. Since this can collide with discussing code, think of the use case to determine what you're talking about. Are you:

* discussing the number only in your exposition? Use the English form. 
* discussing an integer value from your code? Put the digit `10` in a code snippet. 
* discussing an abstract count that's relevant to your code? Do both, by presenting it as ten (10) or ten (`10`).


### *exampla gratia* (e.g.) vs. *id est* (i.e.), vs. *et cetera* (etc.)

* e.g. — Latin for "given example(s)" — points to a single example or a finite list of examples.
* i.e. — Latin for "meaning" — points out a further explanation of the same idea.
* etc. — follows one or several examples pulled from a longer set of potential examples. 

*etc. and e.g. should not be combined in the same list*

### Disambiguation of "learn"

Because of our appropriation of the word "learn" among our curriculum software, disambiguating its use is important:

* learn — verb — to gain knowledge or improve a skill. 
* `learn` command, the — noun phrase (as, "the `learn` command") — the bash command that runs RSpec tests in Ruby labs. This should always be wrapped in a code snippet.
* Learn.co — proper noun — the website and address of the curriculum tool available to students, faculty, and staff.
* Learn App, the — proper noun — the Mac OS X app the integrates with testing and Learn.co.

Usage:

"You'll learn that the `learn` command integrates with your profile on Learn.co by uploading information through the Learn App."

#### Learner vs. learner

* learner — noun — a person who is gaining new knowledge or developing a skill.
* Learner — proper noun — a student using Learn.co to learn software development.

Usage:

"Learners on Learn.co are learning the tools to make themselves lifelong learners."

### Tables

Tables are a great way to organize sets of parallel information, such as [logical operators](https://github.com/learn-co-curriculum/reading-ios-looping-and-conditionals#combining-conditionals).

Try to keep the markdown symbols as table-like as possible, wrap symbols in code snippets, and use markdown reference notation for icon links inside a "cell". These will improve future maintainability of the code.

## Links

Hyperlinks:

`[Text to display](http://url)`

renders as

[Text to display]()

Image links:

`![Image name that does not show](http://url)`

#### Reference Notation

A reference link can be declared elsewhere in the code using the following notation to give a symbolic name to the URL, but this line will be hidden to the viewer:

`[reference_link]: http://url`

Then, hyperlinks and image links can utilize the reference link by using square brackets (`[` `]`) around the reference name like this:

Hyperlink:
`[Text to display][reference_link]`

Image link:
`![Image name][reference_link]`
