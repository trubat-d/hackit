---
description: Bell-lapadula, Biba, Clark-wilson
---

# Security Models

## Bell-Lapadula Model

The Bell-Lapadula model can be understood through a corporate office scenario:

* Employees have different security clearance levels (e.g., intern, regular employee, manager, executive)
* An intern can't access confidential executive documents (no read up)
* An executive can't save sensitive information to a public folder accessible by all employees (no write down)

This ensures that sensitive company information is only accessible to those with appropriate clearance, maintaining confidentiality across the organization.

## Biba Model

The Biba model, in contrast to Bell-Lapadula, focuses on data integrity rather than confidentiality. It can be illustrated through a software development environment:

* Developers have different integrity levels (e.g., junior, senior, lead developer)
* A junior developer can't modify critical system components (no write up)
* A lead developer shouldn't read potentially corrupted data from untrusted sources (no read down)

## Clark-Wilson Model

The Clark-Wilson model focuses on maintaining data integrity in commercial systems. It introduces the concept of well-formed transactions and separation of duties. For example:

* In a banking system, a single employee can't both initiate and approve a large transaction
* Data can only be modified through predefined procedures, ensuring consistency and preventing unauthorized changes

### Constrained Data Items (CDIs) and Transformation Procedures (TPs)

Let's explain these concepts using a simple example of a library system:

* **Constrained Data Items (CDIs):** Think of these as the books in the library. They are important items that need to be protected and managed carefully.
* **Transformation Procedures (TPs):** These are like the library's rules for checking out or returning books. They're the only ways you're allowed to change information about the books.

For example, when you borrow a book:

* The book (CDI) can only be checked out using the proper checkout process (TP).
* You can't just take a book without following this process, as it would break the library's rules.

### Integrity Verification Procedures (IVPs)

Continuing with our library example:

* **Integrity Verification Procedures (IVPs):** These are like the librarian's regular checks to make sure all books are where they should be and in good condition.

For instance:

* The librarian might do a weekly inventory check to ensure all books are accounted for.
* This process helps maintain the accuracy of the library's records and catches any mistakes or issues.
