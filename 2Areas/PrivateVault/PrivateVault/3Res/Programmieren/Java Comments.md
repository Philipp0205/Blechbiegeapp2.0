
https://www.baeldung.com/java-clean-code

[Code comments](https://www.baeldung.com/cs/clean-code-comments) can be **beneficial while reading code to understand the non-trivial aspects**. At the same time, care should be taken to **not include obvious things in the comments**. This can bloat comments making it difficult to read the relevant parts.

Java allows two types of comments: Implementation comments and documentation comments. They have different purposes and different formats, as well. Let's understand them better:
-   Documentation/JavaDoc Comments
    -   The audience here is the users of the codebase
    -   The details here are typically implementation free, focusing more on the specification
    -   Typically useful independent of the codebase
-   Implementation/Block Comments
    -   The audience here is the developers working on the codebase
    -   The details here are implementation-specific
    -   Typically useful together with the codebase

So, how should we optimally use them so that they are useful and contextual?

-   Comments should only complement a code, if we are not able to understand the code without comments, perhaps we need to refactor it
-   We should use block comments rarely, possibly to describe non-trivial design decisions
-   We should use JavaDoc comments for most of our classes, interfaces, public and protected methods
-   All comments should be well-formed with a proper indentation for readability


