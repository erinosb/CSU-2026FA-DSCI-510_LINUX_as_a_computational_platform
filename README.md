# DSCI510: LINUX as a computational platform

## Welcome to 'Linux as a Computational Platform'!

Linux/Unix is the primary platform for computational science. The goal of this course is to train scientists in its use, with particular emphasis on the needs of bioinformatics users. The course covers basic Linux commands and utilities, running and managing computational jobs, and handling and manipulating large biological datasets.

<p align="center">
<img width="410" alt="linux_logo" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/linux_logo.png">
</p>


Please read the [Syllabus](#syllabus) below for classroom information and content that will be covered throughout the class. 

Please see the [Modules](01_modules) directory for specific content being covered.

Please see the [Computer Requirements](04_resources/Computer_Requirements.md) for important information prior to class. 

----
# Schedule

| Date  | Module | Description | Reading | Assignments |
|-------|------|-------------|---------|-------------|
| August 25 | [week1](01_modules/Week1) | Course introduction, The terminal, Navigating the file system | Chapters 1, 2 | Assignment 1 **(due September 1)**|
| August 27 | [week1](01_modules/Week1) | Paths, Options, Working with files 1 (more, less, head, tail, wc), Wildcards, Getting help | Chapter 2 (navigation), Chapter 3 (ls, less), Chapter 4 (wildcards) | Assignment 2 **(due September 1)** |
| Bonus Content | 1 | TBD | | |
| September 1 | [week2](01_modules/Week2) | Making & removing, Copying & moving, File transfer, File formats | Chapters 4-5 (mkdir, cp, mv), Chapter 6 (redirection), Chapter 16, Chapter 18 (gzip) | Assignment 3 **(due September 8)** |
| September 3 | [week2](01_modules/Week2) | Redirection, Working with files 2 (cat, grep, cut), Practice grep & cut, Pipes, More Pipes | Chapter 19 (grep), Chapter 20 (sort, uniq, cut), Chapter 5 (alias), Chapter 9 | Assignment 4 **(due September 8)** |
| Bonus Content | 2 | TBD | | |
| September 8 | 3 | Working with files |  | Assignment 5 **(due September 15)** |
| September 10 | 3 | Scripting 1 |  | Assignment 6 **(due September 15)** |
| Bonus Content | 3 | TBD |  | |
| September 15 | 4 | Scripting 2 |  |  |
| September 17 | 4 | Scripting 3 |  |     |
| Bonus Content | 4 | TBD | | |
| **Final Exam** | **5** | **FAQ on Exam project, Tips & Tricks 1** | **Examples of past projects**  | **Exam Project (due September 22)** |


----

# Syllabus

Linux/Unix is the primary platform for computational science. The goal of this course is to train scientists in its use with particular emphasis on the needs of bioinformatics users. The course covers basic Linux commands and utilities, running and managing computational jobs, and handling and manipulating large biological datasets.

## Contents

- [Course Objectives](#course-objectives)
- [Time & Place](#time-and-place)
- [Attendance](#attendance)
- [Code Club](#code-club)
- [Prerequisites](#prerequisites)
- [Textbook](#textbook)
- [Instructor](#instructor) 
- [Grading](#grading)
- [Assignments](#assignments)
- [Student Disability Accommodations](#student-disability-accommodations)
- [Other Accommodations](#other-accommodations)
- [Privacy Policy](#privacyposting-policy)
- [Expectations](#expectations)
- [Health & Safety](#health-and-safety)
- [AI Statement](#ai-statement)
- [Additional Documents](#additional-documents)
  - [Erin's Teaching Statement](04_resources/Nishimura_TeachingStatement_260819.pdf)
  - [Campus Resources](04_resources/Resources_Nishimura_260819.pdf)

## Course Objectives

<ins>By the end of the course, students will:

- Be comfortable with the Linux command line and command-line programs, including the ability to move, create, or edit files and directories
- Know how to search, manipulate, and process large datasets
- Write and execute small bash script programs
- Be aware of High Performance Computing resources and how they are used. 


## Time and Place

**Come to class:** The lectures will be very interactive with individualized help only available in the classroom, so in-person attendance is encouraged. <ins>The course starts on Tuesday, August 25th, 2026 and ends on Thursday September 17th, 2026. 

**Lectures:** Tuesdays and Thursdays, 10:00 - 11:50 am in AZ building, room E210

**Class Recordings:** Lectures recorded and posted to canvas after class. Due to a lengthy zoom-to-canvas conversion, videos will not be available until late afternoon or the following day. Please note, this process is not perfect and subject to some failure. Please respect the privacy policy (below) regarding these recordings. Please note - coming to class is the best way to learn!

## Attendance

Class attendance is not mandatory, but please let me know if you will be attending multiple classes remotely or making them up at a later time. I just want to make sure I know who is still engaged.

## Code Club

Because this course is so flexible, it puts a lot of responsibility on you to ensure you are keeping up with the class content. My office hours for this class will be during **Code Club**, so on **Fridays from 10 am - 11 am in AZ E210**. Please come, and don't feel like you need to have dedicated questions. You can show up to do your homework, or chip away at your final projects, or solicit any advice.

## Prerequisites

Students do not need to have any prior experience in computing, programming, or coding.

Graduate standing is encouraged but not required. An interest in using LINUX/UNIX in your research work is encouraged. We will focus on using LINUX/UNIX to support research primarily in the life sciences. However, the content is broadly applicable to many fields.

**BEFORE** the first day of class, ensure you have purchased, uploaded, or installed all the required hardware and software. See [Computer Requirements](04_resources/Computer_Requirements.md).

## Textbook

The textbook is optional. Due to the variable nature of LINUX instruments, not all the examples that work in the textbook will work on your computer. 

The textbook is **The Linux Command Line** by William Shotts. Though this book is available for purchase (Currently 7th ediction), the 7th edition is available for free here: [The Linux Command Line](https://sourceforge.net/projects/linuxcommand/files/TLCL/25.12/TLCL-25.12A.pdf/download)

I have also included a copy of the .pdf under our resources area within this github repository:

  - [The Linux Command Line, 7th edition](04_resources/TLCL-25.12A.pdf)

The book is available as a **free, downloadable pdf** from the book website (also attached above) or as a paperback widely sold by booksellers.

## Instructor

Erin Osborne Nishimura, PhD	(she/her)

Department of Biochemistry & Molecular Biology

Cell and Molecular Biology Professor

erinnish@colostate.edu or canvas e-mail

**NOTE:** I ask for your patience throughout the class as there will be bumps in the road, that is just the way it goes. 

Please e-mail me with any questions through regular e-mail or canvas e-mail. Course content-related questions that are e-mailed to instructors may be posted (anonymously) on Canvas Discussions for a faster response and to broadcast insight to the group. Personal or individual concerns will not be disclosed in that way.

## Grading

Your grade for this course will be based on assignments, participation, and a final exam. The percentages are as follows:

- Assignments: 35.5 %
- In Class Quizzes: 30 %
- Final exam: 35.5 %

The calculation of the final letter grade will be made as follows:

- A+: 98.0 - 100.0%
- A: 90.0 - 97.9 %
- B+: 88.0 - 89.9%
- B: 80.0 - 87.9 %
- C: 70.0 - 79.9%
- D: 60 - 69.9%
- F: below 60%

## Assignments

- Assignments make up 35.5 % of your course grade.
- There will be **6 assignments**. Assignments must be turned in on Canvas by 11:59 pm on the due date. 
- If you need to turn in an assignment LATE, please talk to me and request additional time before the due date. You may turn in an assignment up to **48 hours late** but only with **PRIOR** approval!

## Student Disability Accommodations

SDC accommodations: I recognize that the Student Disability Center is behind in issuing accommodation letters. If you have a situation that requires SDC accommodations, please e-mail me directly and we can make arrangements. You can do this even before your official paperwork is processed in the SDC. This class has a lot of flexibility for all students with or without letters.

## Other Accommodations

This class is aimed at graduate students beyond their first year of coursework. As such, I realize students are engaged with research and exams. This class is designed to be sufficiently flexible to accommodate a reasonable number of absences and other time commitments. However, please be aware that you also have other options, such as auditing the class.

To audit the class, you do 1) come to class as you like, 2) do the activities as you like, 3) participate as you like. Auditors do NOT enroll, receive credit, receive a final grade, turn in assignments, or receive feedback on assignments. Please let me know quickly if this is an attractive option for you, as the withdrawal date for this class is the first week.

## Privacy/Posting Policy

The instructor **does not** permit the distribution of course material. This means you are not permitted to post course content, course videos, or representations of the class online. We are offering recordings for students to assist them in learning. Please be respectful of people's privacy with these recordings and content.

## Expectations

You are expected to be familiar with the [Student Code of Conduct](https://resolutioncenter.colostate.edu/conduct/code/). This course will adhere to the [CSU Academic Integrity Policy](https://resolutioncenter.colostate.edu/conduct/academic-integrity/). At a minimum, violations will result in a grading penalty in this course, a report to the Office of Conflict Resolution and Student Conduct Services, and communication with your professor and/or graduate program director.

Colorado State University has clear [Principles of Community](https://inclusiveexcellence.colostate.edu/about/principles-of-community). We each have the responsibility to uphold these values as we interact with one another and learn.

Please know that use of GradeBuddy, Chegg, Course Hero, or other web services that market themselves as tutoring or study guides are not permitted in this course. Many instances of their use are a violation of the Student Integrity Policy. Please note that Plagiarism will not be tolerated. Learn more through [Academic Misconduct Resources](https://tilt.colostate.edu/integrity/studentresources/).


## Health and Safety

Don't feel pressured to come to class if you are ill. Staying home when you are sick prevents the spread of disease. If this happens, you can use the recorded options. 


## AI Statement

*Things may change in future classes. Other professors will have different statements.*

I implore everyone to think deeply about their own **personal goals** for this class. What do you want to master? What do you want to take with you after you leave?

Chances are, you want to gain a **skillset** to apply to your research and career.

The best practices for learning new skills are to **practice, struggle, experiment, spend time, think deeply, and sit with the material.**

AI has advantages and disadvantages in this learning process.

**Beneficial usage and suggestions:**

Beneficial usage and suggestions:
  - **Conversational:** A prompt like “Teach me how to use a for loop in bash scripting” can organize information succinctly without ads.
    - Warning: information is not always accurate
  - **Grammar & Light editing:** Using AI to decode tricky English turns-of-phase or assist with grammar and clarity. Please use caution as AI tools have a tendency to change the meaning of your words, not just the wording.
  - **Coaching:** You can use AI to coach you through hard sections once you have tried to work them out on your own. You can use AI to explain why something isn’t working. These coaching, learning, and refinement tasks are ok.
  - **Extension:** You can use AI to write sections of your exam project that are beyond the scope of this course. Just document these sections. 

**Disallowed usage:** 

  - Generative usage is NOT allowed – Do not use AI to de novo write your code for assignments or the final project, as this can negatively impact learning. 
  - Using AI on the quizzes is not allowed.

**Unsure about what is ok and not ok?**

You can always e-mail me to ask. Also, if you would like to disclose your usage of AI in any assignment or in the Exam Project, I encourage you to do so. You can include a statement like…
  - I did not use AI for this assignment.
  - AI helped with grammar and readability, but the original writing was my own.
  - AI helped with idea generation, but I wrote the assignment myself.
  - A small amount of my work (just a couple of sentences) was written by AI.
  - AI wrote a significant portion of this work, but I edited it.

**AI is a part of coding and it is evolving**

I also acknowledge that AI has become a large part of the coding experience and your usage of it will evolve over time. The restrictions here are meant to foster learning within the scope of this class, and are not meant as general best practices to follow after the class concludes. 


**Reach out if you need more time** 

Please contact me if you are feeling overwhelmed or getting behind in the class. I'd rather give you the opportunity to learn the content than put you in a situation where you feel you need to speed through without learning using AI tools.

## Additional Documents

  - [Erin's Teaching Statement](04_resources/Nishimura_TeachingStatement_260819.pdf)
  - [Campus Resources](04_resources/Resources_Nishimura_260819.pdf)