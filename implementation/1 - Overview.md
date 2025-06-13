# 1 - Overview

ICmd contributors are supposed to finish reading the implementation document to know the design and principle of the entire project.

## 1.1 - Principles

### Lazy and Reactive

Different from other desktop frameworks, ICmd lazily computes and avoids repeated computations in its renderer, layouts and components. Instead of callbacks, ICmd complies with the principles of responsive programming to construct a program, making it intuitive to hold all components with functional dependency.

### Efficient

ICmd only makes necessary steps to minimize load on computation. It is contributed by the usages on terminal platforms and restrictions of standard output devices to be as efficient as possible. On the one hand, ICmd renders every frame with the most compressed bytes. On the other hand, It stays highly fast on dispatching and handling events and arranging layouts.

### Universal Compatibility

As a command-line UI framework, it shows the margin on its friendliness to all command-line environments such as servers, BIOS and embedding systems, achieving the minimized dependencies.

## 1.2 - Structure

### Backend
