# Part 1: Are people getting tired of POSIX?

Question:

Are people starting to get tired of POSIX?

Examples include the creators of:

- Fish shell
- Nushell
- Elvish

# Answer (with my small edits):

Yes. There is a real trend, but it is more accurate to describe it this way:

People are not necessarily tired of POSIX itself. Rather, they are getting tired of the limitations and compromises required to maintain POSIX compatibility.

For decades, command-line shells have been built around several fundamental ideas:

- Passing text between processes using pipes.
- Using stdout and stderr as communication channels.
- Working primarily with strings instead of structured, strongly typed objects.
- Using syntax inherited from older shells, such as the Bourne Shell.
- Combining small Unix utilities through text-based pipelines.

This approach is powerful because of its simplicity, composability, and backward compatibility.

However, it also has limitations when building modern development and automation environments.

This is where Fish, Nushell, and Elvish become interesting.

---

## Part 2: Three approaches to modern shells

### 2.1 Fish shell

Philosophy: User experience first.

Fish does not attempt to be POSIX-compatible at all costs.

Its design prioritizes usability and expressiveness over strict compatibility.

Main characteristics:

- Intelligent autocompletion.
- Syntax highlighting.
- Suggestions while typing.
- Readable syntax.
- Convenient interactive features.

Fish primarily attempts to improve the human interface to the command line.

### 2.2 Nushell

Philosophy: Change the data model.

Traditional Unix pipelines primarily transfer text.

Nushell takes a different approach: it transfers structured data.

Examples of structured data include:

- Tables.
- Records.
- Lists.
- Typed values.

This makes working with JSON, CSV, and other structured formats much more natural.

For example, instead of combining grep, awk, and sed to extract information from text, Nushell can work directly with structured records and their fields.

Nushell does not aim to be POSIX-compatible.

Its approach is fundamentally different from traditional Unix shells. 

In a sense, the authors of Nushell try to "re-invent" the Unix shell concept or the shell concept itself, 
  but in a way that is more aligned with common users and the different types of structured data that have become standardized.

### 2.3 Elvish

Philosophy: A shell should also be a modern programming language.

Elvish introduces more advanced programming concepts into the shell environment.

Its features include:

- Data structures.
- Functions.
- Modules.
- More expressive programming capabilities.

Rather than simply extending traditional shell syntax, Elvish attempts to provide a better programming language for command-line work.

---

## Part 3: Why is this happening?

There are several important reasons.

### 3.1 The world has changed

JSON, APIs, containers, Kubernetes, and cloud infrastructure have become part of everyday development.

Raw text is not always the best interface for exchanging data.

### 3.2 Shells have become programming languages

People increasingly write complex logic in shell environments.

This includes:

- Functions.
- Conditions.
- Loops.
- Automation.
- Data processing.

However, traditional shells such as Bash still carry many historical conventions and limitations.

### 3.3 The lack of a modern type system

A string, number, Boolean, record, and list are fundamentally different types of data.

Traditional POSIX shell scripting does not naturally distinguish between these types.

### 3.4 Backward compatibility limits innovation

When changing existing behavior might break millions of scripts, changing the language becomes difficult.

Backward compatibility is valuable, but it can also restrict innovation.

---

## Part 4: Is this really a movement against POSIX?

Not exactly.

There are several different philosophies:

Traditional shells:
- Bash
- Dash
- Zsh

Their priorities include compatibility, established conventions, and the existing Unix ecosystem.

Fish:
- Prioritizes usability over strict POSIX compatibility.

Nushell:
- Prioritizes structured data instead of text-only pipelines.

Elvish:
- Attempts to provide a modern programming language within a shell environment.

Oil / YSH:
- Attempts to modernize shell scripting while maintaining compatibility where possible.

An interesting development in this area is the discussion surrounding the future of shells, including research presented at HotOS 2021.

One important observation is that the problem is not necessarily limited to shell language design. The surrounding ecosystem also influences what can realistically change.

---

## Part 5: The deeper conceptual change

Historically, the Unix shell was understood approximately as follows:

"A shell is a layer of glue that connects programs through text."

Today, an increasingly common perspective is:

"A shell is a programming and automation environment with access to the operating system and external processes."

This is a significant conceptual shift.

POSIX is still extremely important.

It provides portability across systems, and a large amount of existing infrastructure depends on it.

Even users of Fish and Nushell still need to interact with traditional Unix programs.

A possible future is a gradual separation into two worlds:

1. POSIX and traditional shells for portability, infrastructure, and system scripts.
2. Modern shells for interactive work, automation, data processing, and development.

Nushell is particularly interesting because it asks a more fundamental question:

"What if we designed a Unix shell today without assuming that everything must be a string?"

This is not merely an evolution of Bash.

It is a reconsideration of what a shell should be.

---

# Final perspective

The evolution of shells is about more than syntax.

It is about reconsidering the fundamental relationship between:

- Processes.
- Data.
- Pipelines.
- Programming languages.
- The operating system.

Traditional Unix shells are built around text and process composition.

Modern shells are increasingly exploring structured data, better programming abstractions, and improved user experiences.

Both approaches have important strengths, and they are likely to coexist for a long time.
