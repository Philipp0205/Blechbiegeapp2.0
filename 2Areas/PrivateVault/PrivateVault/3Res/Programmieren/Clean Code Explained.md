# Clean Code Explained – A Practical Introduction to Clean Coding for Beginner
Source: https://www.freecodecamp.org/news/clean-coding-for-beginners/
Refs: [[!Clean Code]]
Tags: #arcicle #programmieren #clean-code 

---

>"Any fool can write code that a computer can understand. Good programmers write code that humans can understand."                                       
>– Martin Fowler

## How to name variables
> "There are only two hard things in Computer Science: cache invalidation and naming things."
> – Phil Karlton                                                                                                              
### Use meaningful Names
- Do not use comment to explain how variable is used
- "A name should tell you why it exists, what it does, and how it is used. If a name requires a comment, then the name does not reveal its intent." - Clean Code

### Avoid Disinformation
- Do not used dataType for variables name
- If there is an ArrayList with do not name the variable "list"

### Do not use noise word
- lile object, data, variable, object, Manager

### Use Pronouncable Names
- `currentDate` is better than `yyymmdstr`

### Use Searchable Names
- Do not use magic numbes in code. Just make a var for it. 

```
if (student.classes.length < 7) {
   // Do something
}
```
Inseatd of "7" use var `MAX_CLASSES_PER_STUDENT`

### Be consistent
- Reuse methods instead of writing new ones

## How to write functions
### Keep them small
- Less than 10-20 lines

### Make sure they just do one thing
> Functions should do one thing. The should do it well. They shoud do it only. 
> - Clean Code

### Encapsulated Conditionals in Function
- Refactoring a condition and putting it into a named function is a good way to make your conditionals more reable. 
- See [[Refractoring Kurs#Recipe 1 Extract Method]] and [[Refractoring Kurs#Recipe 4 Conditionals and Loops]]

### Fewer Argument
- Functions shouldh ate tow or fewer arguemtns, the fewer the better. 

### Do not se Flar Arguments
- A flag arugmetn is a bollean arugment that is passed to a function. Two different actions are taken depending on the value of this argument
- Flag arguemnt natually contradict the principle of single responsibility. When you see them, you should consider dividing the function into two.

Bad:
```
public Booking book (Customer aCustomer, boolean isPremium) {
      if(isPremium) 
       // logic for premium book
      else
       // logic for regular booking
    }
```

### Do Not Have Side Effects
- Side effects are unintended consequeces of your code. 
- For example the may be changing the passed parameters, in case of passign by refencer, or maybe changing  a global variable.

### Don't Repeat Yourself
- Code repetition may be the root of alle evil in software. 
- Duplicate code means you need to change things in multiple places when there is a change in logic and it is very error prone.





