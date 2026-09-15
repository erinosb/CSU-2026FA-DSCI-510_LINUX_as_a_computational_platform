

# Scripting 3 - Control Flow

## Todays objectives: 

<details>
  <summary>Click to expand/collapse</summary>

---

- **Vocabulary**
  - Control flow
  - Sequences
  - Conditionals (also called selections)
    - test statement
    - conditional operator
  - Loops
    - counter vaiable
    - initialization
    - condition
    - incrementalization

- **Things you should know how to do after this class**
  - Be able to differentiate sequences, conditionals, and loops
  - Write a basic conditional statement using "if"
  - Write a basic conditional statement using "for"
  - Be able to use a string operation to replace file extensions
  - Be able to loop over a list of arguments supplied to the script using "$@"

- **Commands covered**
  - String operations:
    - `newvar=${oldvar/a/A}`
    - `newvar=${oldvar//a/A}`
    - `newvar=${oldvar/#To/So}`
    - `newvar=${oldvar/%txt/fastq}`
    - `newvar=${oldvar:3}`
    - `newvar=${oldvar:3:4}`
  - `if`
  - `else`
  - `elif`
  - `for`
  - `while`

---

</details>


## Reminder: 

 - HW 5 and 6 are due today
 - Quiz 6 - Last one!
 - Course Survey

----

## Control Flow

All the software we use in every aspect of our lives is running some sort of code in the background. Surprisingly, the vast majority of that code can be broken down into three simple programming structures: 1) **sequences**, 2) **conditionals**, and 3) **loops**. Together, these are the big three of **control flow** which refers to the concept of how code is wired together and the order in which blocks of code run.

<p align="center">
<img width="70%" alt="controlFlow" src="../../05_images/sequence_cond_loops.png">
</p>

----

## Sequences

**Sequences** are actions that are completed in a specific order. **A** must be done first. Next **B**. Then **C**. Sequences are complete when all the actions in the sequence are complete.

Example:
- wake up
- take shower
- get dressed
- eat breakfast

In LINUX, the order of sequenced operations is dictated by the order of the lines of code. Each line is executed one at a time.

----

## Conditionals 

**Conditionals** (sometimes also called **selections**) are forks in the road. A question is asked and depending on the answer, either action **A** or **B** is chosen.

Example:
- If it's a weekday → go to the lab
- If it's a weekend → clean the house

In LINUX, conditionals are specified by `if` statements.

----

## Loops

**Loops** are similar to conditionals in that they also ask a question. However, the difference is that loops ask the same question over and over and over again until a set criterion is satisfied.

Example: Hammering a nail
- You ask - is the nail hammered in? No → hit the nail
- Now is the nail hammered in? No → hit the nail
- Now is the nail hammered in? No → hit the nail
- Now is the nail hammered in? No → hit the nail
- Now is the nail hammered in? No → hit the nail
- Now is the nail hammered in? No → hit the nail
- Now is the nail hammered in? Yes → stop hammering

In LINUX, there are different types of loops: `while`, `for`, `until`, and `select`. In the interest of time, we will only cover `while` and `for`.

These three structures are each very simple on their own, but combined together, a sophisticated complexity emerges.

Continue on to [Conditionals](4-2_Conditionals.md)
