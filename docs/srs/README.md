# Software Requirements Specification (SRS)

| Document field   | Value                                             |
| ---------------- | ------------------------------------------------- |
| Document version | 0.1                                               |
| Prepared by      | Milad Mazhari                                     |
| Reviewer         | Abolfazl Sadeghian                                |
| Contributors     | Milad Mazhari, Mehran Sadeghi, Abolfazl Sadeghian |

---

## 1. Introduction

### 1.1 Purpose

This document defines the initial scope, users, functional requirements, non-functional requirements, assumptions, and constraints of Dice, a web-based Personal Expense Management System. It is intended to provide a common reference for the team during analysis, design, implementation, and verification.

### 1.2 Product Overview

Dice is a multi-user web application intended to help individuals record and manage their personal income and expenses. Users will be able to organize expense records into categories, review transaction history, search and filter financial records, and view summaries and statistics about their financial activity.

Each registered user is expected to manage their own financial records. One user's records must not be visible or editable by another user.

### 1.3 Requirement Language and Identifiers

The word **shall** indicates a mandatory requirement. The words **should** and **may** indicate recommendations and optional capabilities, respectively.

Requirements use stable identifiers:

- `FR-n`: Functional Requirement.
- `NFR-n`: Non-Functional Requirement.
- `UC-n`: Use Case.

---

## 2. Scope

### 2.1 In-Scope Features

The initial project scope includes:

1. **User registration and login:** Users can create accounts and authenticate to access the application.
2. **Expense management:** Users can add, view, edit, and delete their own expense records.
3. **Income management:** Users can add, view, edit, and delete their own income records.
4. **Expense categories:** The system provides predefined categories and allows users to create custom categories for their personal use. Each expense must belong to exactly one category. 
5. **Transaction history:** Users can review their recorded income and expenses.
6. **Search and filtering:** Users can find records using supported search criteria and filters.
7. **Reports and statistics:** Users can view summaries of income, expenses, and the resulting balance for a selected period.

### 2.2 Out of Scope for the Initial Version

- Budget creation, budget limits, and budget alerts.
- Bank-account integration or automatic transaction imports.
- Online payments, money transfers, or bill payment.
- Native Android or iOS applications.
- Automatic recurring transactions.
- Data export to PDF, CSV, or spreadsheet files.
- Notifications and reminders.
- Multi-currency conversion and exchange-rate services.
- Editing and deleting custom expense categories.
- Categorizing income records.

### 2.3 Scope Boundary

Dice is a personal financial record-management application. It records information entered by users; it is not intended to connect to banks, execute financial transactions, or provide financial advice.

---

## 3. Users and Stakeholders

### 3.1 Guts (Guest User)

A Guts is a person who has not authenticated. A Guts may access account registration and login functions but must not access private financial records or authenticated application features.

### 3.2 Cowboy (Registered User)

A Cowboy is an authenticated person who can manage their own income and expense records, categories, transaction history, searches, filters, and reports.

### 3.3 Development Team

The development team is responsible for analyzing, designing, implementing, and documenting Dice.

---

## 4. Assumptions and Constraints

### 4.1 Assumptions

- Dice will be accessed through a web browser.
- Multiple users (Cowboys) will have separate accounts.
- Users (Cowboys) will enter their own income and expense information manually.
- Financial records must remain available to their owner after signing out and signing in again.
- Each financial record will be associated with the user who created it.
- The initial application will provide summaries based on the records stored in Dice.

### 4.2 Constraints

- The initial deliverables include software engineering documentation and system models before implementation.
- The technology stack and deployment environment have not yet been selected in this document.

### 4.3 Decisions Requiring Team Agreement

The following details are not yet settled and must not be treated as final design decisions:

1. Whether users register with an email address, username, or another identifier.
2. Whether email verification and password-reset functionality are required.
3. Which fields are mandatory for an expense and for an income record.
4. Whether income records also have categories or income-source labels.
5. Which date ranges and breakdowns are available in reports.
6. The exact search fields and filter options.
7. Whether deleted records are permanently removed or retained as soft-deleted records.

---

## 5. Functional Requirements

### 5.1 Account Management and Authentication

| ID    | Requirement                                                                                                                   | Priority |
| ----- | ----------------------------------------------------------------------------------------------------------------------------- | -------- |
| FR-01 | The system shall allow a Guts (guest) to create a user account by providing the required registration information.            | Must     |
| FR-02 | The system shall allow a Cowboy (registered user) to log in using their registered credentials.                               | Must     |
| FR-03 | The system shall allow a Cowboy (authenticated user) to log out.                                                              | Must     |
| FR-04 | The system shall prevent Gutses (guests) from accessing pages and operations that expose or modify private financial records. | Must     |
| FR-05 | The system shall associate each user's financial records with that user's account.                                            | Must     |

### 5.2 Expense Management

| ID    | Requirement                                                                                        | Priority |
| ----- | -------------------------------------------------------------------------------------------------- | -------- |
| FR-06 | The system shall allow a Cowboy (authenticated user) to create an expense record.                  | Must     |
| FR-07 | The system shall allow a Cowboy (authenticated user) to view their own expense records.            | Must     |
| FR-08 | The system shall allow a Cowboy (authenticated user) to edit their own expense records.            | Must     |
| FR-09 | The system shall allow a Cowboy (authenticated user) to delete their own expense records.          | Must     |
| FR-10 | The system shall prevent a user from viewing, editing, or deleting another user's expense records. | Must     |

### 5.3 Income Management

| ID    | Requirement                                                                                       | Priority |
| ----- | ------------------------------------------------------------------------------------------------- | -------- |
| FR-11 | The system shall allow a Cowboy (authenticated user) to create an income record.                  | Must     |
| FR-12 | The system shall allow a Cowboy (authenticated user) to view their own income records.            | Must     |
| FR-13 | The system shall allow a Cowboy (authenticated user) to edit their own income records.            | Must     |
| FR-14 | The system shall allow a Cowboy (authenticated user) to delete their own income records.          | Must     |
| FR-15 | The system shall prevent a user from viewing, editing, or deleting another user's income records. | Must     |

### 5.4 Expense Categories

| ID    | Requirement                                                                                                                                   | Priority |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| FR-16 | The system shall provide a predefined set of expense categories.                                                                              | Must     |
| FR-17 | The system shall allow an authenticated user to create custom expense categories for personal use.                                            | Must     |
| FR-18 | The system shall allow an authenticated user to assign exactly one predefined category or one of their own custom categories to each expense. | Must     |
| FR-19 | The system shall display the category associated with an expense when displaying that expense.                                                | Must     |
### 5.5 Transaction History, Search, and Filtering

| ID    | Requirement                                                                                                    | Priority |
| ----- | -------------------------------------------------------------------------------------------------------------- | -------- |
| FR-20 | The system shall provide a Cowboy (authenticated user) with a history of their own income and expense records. | Must     |
| FR-21 | The system shall allow a Cowboy to search their records using the search fields approved by the team.          | Must     |
| FR-22 | The system shall allow a Cowboy to filter their records using the filter criteria approved by the team.        | Must     |
| FR-23 | Search results and filtered results shall contain only records belonging to the Cowboy (authenticated user).   | Must     |

> The exact search fields and filter criteria must be agreed upon before the detailed design is finalized.

### 5.6 Reports and Statistics

| ID    | Requirement                                                                                                                 | Priority |
| ----- | --------------------------------------------------------------------------------------------------------------------------- | -------- |
| FR-24 | The system shall calculate the total income recorded by the Cowboy (authenticated user) for a selected reporting period.    | Must     |
| FR-25 | The system shall calculate the total expenses recorded by the Cowboy (authenticated user) for a selected reporting period.  | Must     |
| FR-26 | The system shall calculate the balance for a selected reporting period as total income minus total expenses.                | Must     |
| FR-27 | The system shall present the calculated financial summaries to the Cowboy (authenticated user) in an understandable format. | Must     |
| FR-28 | The system shall ensure that reports and statistics use only the Cowboy's (authenticated user's) records.                   | Must     |

> The reporting periods and any additional statistics or charts are open for team agreement.

---

## 6. Non-Functional Requirements

| ID     | Quality Attribute     | Requirement                                                                                                                           | Priority                   |
| ------ | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| NFR-01 | Security              | The system shall require authentication before granting access to a user's private financial records.                                 | Must                       |
| NFR-02 | Authorization         | The system shall enforce ownership checks for every operation that reads or modifies a financial record.                              | Must                       |
| NFR-03 | Credential Protection | The system shall not store user passwords in plain text.                                                                              | Must                       |
| NFR-04 | Data Integrity        | The system shall validate submitted financial-record data before saving it.                                                           | Must                       |
| NFR-05 | Persistence           | Successfully saved records shall remain available to their owner across later sessions, unless the owner deletes them.                | Must                       |
| NFR-06 | Usability             | The user interface shall present clear labels, validation feedback, and operation results.                                            | Should                     |
| NFR-07 | Consistency           | The application shall use consistent terminology and interaction patterns across its pages.                                           | Should                     |
| NFR-08 | Maintainability       | The system design and source code shall be organized so that components can be understood and modified independently where practical. | Should                     |


---

## 7. Use Case Overview

The following use cases summarize the main interactions that will be modeled in more detail during system analysis.

| ID    | Use Case                  | Primary Actor            | Brief Description                                                   |
| ----- | ------------------------- | ------------------------ | ------------------------------------------------------------------- |
| UC-01 | Register Account          | Guts (Guest)             | Creates a new user account.                                         |
| UC-02 | Log In                    | Guts (Guest)             | Authenticates and enters the application.                           |
| UC-03 | Log Out                   | Cowboy (Registered User) | Ends the authenticated session.                                     |
| UC-04 | Add Expense               | Cowboy (Registered User) | Records a new expense.                                              |
| UC-05 | View Expense History      | Cowboy (Registered User) | Reviews previously recorded expenses.                               |
| UC-06 | Edit Expense              | Cowboy (Registered User) | Modifies an existing expense.                                       |
| UC-07 | Delete Expense            | Cowboy (Registered User) | Deletes an existing expense.                                        |
| UC-08 | Manage Income             | Cowboy (Registered User) | Creates, views, edits, or deletes income records.                   |
| UC-09 | Categorize Expense        | Cowboy (Registered User) | Assigns an expense category.                                        |
| UC-10 | Search and Filter Records | Cowboy (Registered User) | Finds records using available search and filter criteria.           |
| UC-11 | View Financial Summary    | Cowboy (Registered User) | Views income, expense, and balance summaries for a selected period. |
| UC-12 | Create Custom Category    | Cowboy (Registered User) | Creates a custom expense category for personal use.                 |

Detailed use-case descriptions and activity diagrams should be developed after the team agrees on this requirements baseline.

---

## 8. Initial Domain Concepts

The following concepts are provided to guide later modeling. They are not a finalized class diagram or database schema.

| Concept           | Initial Meaning                                                  |
| ----------------- | ---------------------------------------------------------------- |
| User (Cowboy)     | A person with an account who owns financial records.             |
| Expense           | Money spent by a user.                                           |
| Income            | Money received by a user.                                        |
| Expense Category  | A classification assigned to an expense.                         |
| Financial Summary | Calculated totals of income, expenses, and balance for a period. |

The class diagram owner should use these concepts as a starting point and propose any additional classes or relationships needed to satisfy the approved requirements.

---

## 10. Glossary

| Term                           | Definition                                                                                         |
| ------------------------------ | -------------------------------------------------------------------------------------------------- |
| Authentication                 | Verifying the identity of a user, for example through credentials.                                 |
| Authorization                  | Determining whether an authenticated user is allowed to access a resource or perform an operation. |
| Expense                        | A record of money spent.                                                                           |
| Income                         | A record of money received.                                                                        |
| Transaction / Financial Record | A general term referring to an income or expense record in Dice.                                   |
| Category                       | A label used to classify an expense.                                                               |
| Reporting Period               | The date range used to calculate a financial summary.                                              |
