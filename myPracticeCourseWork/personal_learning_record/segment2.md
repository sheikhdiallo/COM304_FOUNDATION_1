[Contents](../personal_learning_record/personal_learning_record.md) | [Segment 2 - Languages and OS](../personal_learning_record/segment2.md) 

# Segment 2 - Languages and Operating Systems

---
**NOTE**

For each of the sessions, bullet point notes on what you have learnt.
Use markdown references and / or links to resources you have used
use  screen shots and / or code samples as appropriate.

---

## Session 5 - Computer Languages

Introduction

\-in this session we had a look at computer programming languages and how they interact with the computers hardware.

\-this session will proceed in roughly the following order:

\-Introduction & machine code, assembly code and high-level languages, in session two we saw how combinational logic can be used to create a microprocessor.

\-we saw that the processor supported 12 institutions which could be arranged in the simulators Rom as a very low-level programme.

instructions seen as session 5 binary CPU instructions all referred as machine code

You could enter the binary machine code directly, but this would be time consuming and error prone. Instead, programmers write low level programmes in an equivalent human readable version of the programme called assembly code.

An Assembler is a programme which translates the human readable assembler source code turning into machine code to run on the processor.

Assembly code is very specific to the processor which it targets. It is designed to be easy for a programmer to specify instructions for moving and manipulating data within processor registers and between the processor and external memory.

assembler is not designed to make it easy to understand what the purpose of a programme is but it does allow for the programmers contents which are not part of the programme to help explain what the assembler code is doing.

High level languages

a high-level language such as C, Java, Python Basic or Java script or designed to allow programmers to easily express high level concepts without being concerned about how this translates to the bits and bytes manipulated by the CPU.

A high-level language is translated into low level machine code to run on a processor.

High level languages come into two fundamental flavours; Interpreted languages and compiled languages as illustrated below.

Open and closed source programmes often compiled programmes are shipped by their authors are all pre-compiled machine code which is ready to run the target system.

Machine code can be disassembled into assembler code but without any comments or the original high-level language this is very difficult for someone to understand.

Many companies rely on not distributing the original source code with the machine code.

## session 6

## Session 7

## The Origins of Linux Operating System

In the 70s At&t developed the original C programming language, This was used to write a new operating system called Unix . Unix and C became increasingly popular and computer manufacturers began developing their own variants to run there own workstations;

- HPUX-Hewlett Packard
- Solaris- Sun Microsystems
- AIX- IBM
- Ultrix – Digital Equipment Coporation

The CPU’s underlying these systems were significantly different with IBM hardware using PA-RISC processors Sun using SPARC (Scalable Processor ARChitecture)

In theory, a program written in C to run on a Unix OS could run on any og these variants, However as there were difference this was not the case. Therefore, this lead to the development of the POSIX Compliant Unix standard ( defines a standard threading library API which is supported by most modern operating systems (2008) which standardised the system calls across unix systems.

Similar to this, Richard Stallman who was a researcher at MIT, became annoyed due to the way companies were hiding details of their operating systems through the use of ‘closed source’ therefore keeping the programs private. In 1983 Stallman resigned from MIT and began developing a Unix style operating system which would be free for anyone to use and would be published as an open-sourced program. He also developed a gcc complier and many different software utilities were released as part of the GNU project (A operating system that is free software).

A key innovation was to publish the software under the Copy Left GPL licens e ( a series of widely used free software licences, or copyleft licenses, that guarantee end users the freedoms to run, study, share and modify the software), which forced whoever copied or extended the source code to publish their work under the same license.

During the 1990’s, Linus Torvalds performed a masters project trying to develop a Unix kernel which would work on low cost Intel Processors. He discovered the GNU project in 1991 and realised that the kernel he was developing could be combined with GNU utilities to create a fully open source operating system. (incomplete notes)

## session 8 (consolidate)

TBD

