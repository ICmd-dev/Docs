# 1 Overview

ICmd contributors are supposed to finish reading the implementation document to know the design and principle of the entire project.

## 1.1 Principles

### Lazy and Reactive

Different from other desktop frameworks, ICmd lazily computes and avoids repeated computations in its renderer, layouts and components. Instead of callbacks, ICmd complies with the principles of responsive programming to construct a program, making it intuitive to hold all components with functional dependency.

### Efficient

ICmd only makes necessary steps to minimize load on computation. It is contributed by the usages on terminal platforms and restrictions of standard output devices to be as efficient as possible. On the one hand, ICmd renders every frame with the most compressed bytes. On the other hand, It stays highly fast on dispatching and handling events and arranging layouts.

However, for those embedding devices without standard inputs or outputs, we may have another low-level part to drive the framework with universal interfaces to the physical machine.

### Hierarchical Framework

To keep the framework abstracted from platform-specific settings, the project is divided into several separating parts with certain independence. Roughly they can be the backend(Core things like runtime and system interfaces) and frontend(Development kit and other abstract things)

### Universal Compatibility

As a command-line UI framework, it shows the margin on its friendliness to all command-line environments such as servers, BIOS and embedding systems, achieving the minimized dependencies.

However, for those embedding devices without a operation system, it can be rather tough to implement ICmd runtime on it. So it can't be generally compatible.

## 1.2 Structure

The framework is composed with the following parts which relatively separates each other for safety and abstraction.

### Frontend

Frontend is also known as user level development kit. Here _user_ is who uses ICmd to develop their own command-line softwares. All the surface features like responsive programming and DSL parsers are included in this level. The goal of the frontend is to provide a simplistic and state-of-art experience for developers.

As a set of programming interfaces, it can be used in mainstream script languages like NodeJS and Python.

### Backend

Backend is the core of the framework. It contains implementations from abstract structures to stdout bytes and stdin interactions. Meanwhile, it has to ensure the program well running with all the features. It has to be highly optimized and less dependent.

We use Rust as our language to implement the main part of ICmd.

### Low Level

What if there's no standard output or input? Or it seems platform-specific to achieve what we want? We need a low level as an intermediate part between the physical system and backend, which contains a set of formalized low level interfaces.

We may use a language like C or Zig to achieve this from bare metal.