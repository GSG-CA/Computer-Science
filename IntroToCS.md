# Intro to Computer Science

Computer science is the study of computation, automation, and information. Computer science spans theoretical disciplines, such as algorithms, theory of computation, and information theory, to practical disciplines including the design and implementation of hardware and software

Computer Science Fields:

    1- Data Structures and Algorithms
    2- Programming
    3- Artificial intelligence
    4- Computer networks
    5- Computer security and cryptography
    6- Databases and data mining
    7- Computer graphics and visualization
    8- Image and sound processing

**Algorithms and Data Structures have been called the heart of computer science.**

---

## Data Structure

In computer science, a **data structure** is a particular way of organizing data in a computer memory, so that it can be used efficiently.

#### Why it’s important?

    1- It affect the performance of applications.
    2- Good structure can make application maintenance easier.

---

#### Real Life Example:

A simple example for data structure in real life would be the library.

Library has Books, Articles, Journals and other documents, those could represent **Data**. And there are several **operations** can be done in the library, like adding new books, updating journals or delete documents.

So, with this data structure it will be easy to search for books or lending them. The same goes to adding new books.

---

#### Technical Examples:

- Google use data structures to store data and to process it “Graphs & Vectors”.
- Researchers use data structure to facilitate their work on data “Lists & Maps”.
- Applications like the ones in Paltel and Banks use some kind of data structures “Queue”.

---

### Data Structure & Data Types

- Built-in data types

  Those data types are defined in the programming language, like number, string, boolean.

- User-defined data types

  Those data types are defined by the implementer, we use data types and structure to provide new data type like creating new object for Employee.

#### How data types are related to data structure?

A simple question would be that data types form the domain of data structures.

---

### Data Organizing Principles

#### Ordering

- Put keys into some order so that we know something about where each key is are relative to the other keys.
- Phone books are easier to search because they are alphabetized.

#### Linking

- Add pointers to each record so that we can find related records quickly.

```
E.g. The index in the back of book provides links from words to the
pages on which they appear.
```

#### Partitioning

- Divide the records into 2 or more groups, each group sharing a particular property.

```
E.g. Multi-volume encyclopedias (Aa-Be, W-Z)
E.g. Folders on your hard drive
```

---

### Five Steps per Data Structure

#### \#1 Understanding

- Start with the data structure at the level of concepts and pictures. e.g. visualize a stack and the operations of pushing / popping.

- Understand simple applications.

- Simulate by hand
  e.g., use a stack to reverse the order of letters in a word.

#### \#2 Specification

- Write a specification for a class that could implement the data structure.
- Headings for constructor, public methods, public features
- Includes precondition / postcondition for each method
- Independent of implementation!

#### \#3 Application

- Based on the specification, write small applications to illustrate the use of the data structure.
- “Test the specification” prior to implementation.
- Code not yet compiled / run.

#### \#4 Implementation

- Select appropriate data types.
- Implement as private class vars.
- Write rules relating instance variables to abstract specification.

#### \#5 Analysis

- Correctness.
- Flexibility.
- When possible, compare different implementations of the same ADT.
- Time Analysis
  1- number of operations
  2- big-O notation, e.g., ![](https://i.imgur.com/jWh9p6G.png)

---

## Data Structure Examples

- ### Arrays

  This structure used to store elements in a linear format.

  When it comes to the forms of arrays, we have to forms:

  **Singly Dimensional Array**: store data in one dimension as a single row.

  **Multi Dimensional Array**: store data in different dimensions, mostly in rows and columns.

  **Practical Example**: Storing a contacts list in phones.

- ### Linked List & Doubly Linked List

  It’s a data structure consisting of a group of nodes which together represent a sequence. Under the simplest form, each node is composed of a data and a reference (in other words, a link) to the next node in the sequence; more complex variants add additional links.

  ![](https://i.imgur.com/DFBzssL.png)

  **Practical Example**:Image viewer in windows.

- ### Queues & Stacks

  Queues used to store elements in a way that first stored element stored will be retrieved first, but Stacks retrieve last element first.

  **Practical Example**

  Queues: Adding orderes for printer.
  Stacks: Implementing browser back function.

![Queue](https://i.imgur.com/5sVTQaI.png) ![Stack](https://i.imgur.com/Huw7d86.png)

---

## Algorithms

an **Algorithm** is a finite sequence of well-defined instructions, typically used to solve a class of specific problems or to perform a computation.

or in a simple way an **algorithm** is a set of instructions for accomplishing a task.

an **Algorithm** is a sequence of unambiguous instructions for solving a problem, i.e., for obtaining a required output for any legitimate input in a finite amount of time.

![](https://i.imgur.com/UXYACsg.png)

---

### Finally

**Data Structure** is about how we store data and **Algorithms** is about how we manipulate that data
