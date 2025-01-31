>   **SENG 637 - Software Testing, Reliability, and Quality**

**Lab. Report \#1 – Introduction to Testing and Defect Tracking**

| Group: 5      |
|-----------------|
| Destin Saba                |   
| Cole Cathcart              |   
| Nathan de Oliveira               |   
| Rana El Sadig                |   


**Table of Contents**

- [1 Introduction](#1-introduction)
  - [1.1 Types of Testing](#11-types-of-testing)
- [2 High-level description of the exploratory testing plan](#2-high-level-description-of-the-exploratory-testing-plan)
  - [2.1 Test Type](#21-test-type)
  - [2.2 Scope of Testing](#22-scope-of-testing)
    - [2.2.1 Features to be Tested](#221-features-to-be-tested)
    - [2.2.2 Features Not Tested](#222-features-not-tested)
  - [2.3 Test Logistics](#23-test-logistics)
    - [2.3.1 Who will test?](#231-who-will-test)
    - [2.3.2 When Will testing Occur?](#232-when-will-testing-occur)
- [3 Comparison of exploratory and manual functional testing](#3-comparison-of-exploratory-and-manual-functional-testing)
- [4 Notes and discussion of the peer reviews of defect reports](#4-notes-and-discussion-of-the-peer-reviews-of-defect-reports)
- [5 How the pair testing was managed and team work/effort was divided](#5-how-the-pair-testing-was-managed-and-team-workeffort-was-divided)
- [6 Difficulties encountered, challenges overcome, and lessons learned](#6-difficulties-encountered-challenges-overcome-and-lessons-learned)
- [7 Comments/feedback on the lab and lab document itself](#7-commentsfeedback-on-the-lab-and-lab-document-itself)


# 1 Introduction

This report examines the practical application of manual exploratory, scripted, and regression testing completed in pairs. The System Under Test (SUT) is an ATM simulation system that enables simple bank transactions such as deposits, withdrawals, and transfers using card numbers and PINs.

## 1.1 Types of Testing

To test the ATM simulation system, the following three testing strategies will be used:

- **Exploratory Testing**: Manual, non-scripted testing conducted as per the exploratory testing plan in Section 2.
- **Manual Scripted Testing**: Conducted as per the test suite provided in Appendix C of the assignment documentation.
- **Regression Testing**: Verification of defect fixes in the updated software version.


# 2 High-level description of the exploratory testing plan

The exploratory testing plan covers the functionalities being targeted, the general testing approach, and the methods for generating test cases.

The primary goal of the exploratory testing is to cover all high-level, common use-cases of the system. The primary constraint on exploratory testing is the time available for testing; the team is limited to approximately 30 minutes of exploratory testing per developer.

## 2.1 Test Type

Exploratory testing is a manual, non-scripted form of testing. This testing type involves testers exploring the software without following predefined scripts.   

The exploratory testing will follow a breadth-first approach that targets many use-cases at a high level. The test cases for exploratory testing were generated as per the high level requirements in Appendix B, with a focus on common paths instead of edge cases. We have decided to focus on breadth-first testing of common paths since both in-depth and exceptional path testing will be covered by the manual scripted testing.

## 2.2 Scope of Testing

### 2.2.1 Features to be Tested

We will cover the use cases included in Appendix B: High level requirements:

| Role(s)            | Description |
|--------------------|-------------|
| Operator          | System powers on and requests initial cash |
| Operator          | System powers off but only when not serving a customer |
| Customer          | Logging in with a valid card and PIN |
| Customer          | System locks card after 3 incorrect PIN entries |
| Customer          | Depositing money into any linked account |
| Customer          | Withdrawing money from a linked account in multiples of $20 |
| Customer          | Transferring money between 2 accounts |
| Customer          | Viewing the balance of linked accounts |
| Customer          | Deposit is cancelled if customer does not deposit envelope in time |
| Customer          | System displays transaction errors (other than invalid PIN) and prompts user to make another transaction |
| Customer          | Users can cancel transactions by pressing ‘cancel’ |
| Customer, Operator | The system logs transactions correctly in its internal log |
| Customer          | The system generates receipts with accurate transaction details |

### 2.2.2 Features Not Tested

As this is a high-level test, some features which are mentioned in Appendix C but not in Appendix B may not be covered. In addition, there are other system considerations that will not be tested as they are not included in the high level requirements:

| Feature Not Tested |
|--------------------|
| Encryption of PINs or other sensitive data |
| Secure communication with other systems i.e. the bank |
| Stress testing the system with high transaction volumes or extreme input values |
| Support for different languages or currencies |
| Logical accuracy of backend functions or database operations |
| Performance |

## 2.3 Test Logistics

### 2.3.1 Who will test?

All members of the group will take part in testing, working in pairs of 2. Within each pair, one person will “drive” the program while the other records the outcome of each test. Below we provided a table allocating pairs to certain tests. This might change as we find more bugs that need to be tested.

| Feature              | Pair          |
|----------------------|--------------|
| Power-on            | Cole/Destin  |
| Power-off           | Cole/Destin  |
| Login               | Cole/Destin  |
| Incorrect credentials | Cole/Destin  |
| Deposits            | Cole/Destin  |
| Withdrawals         | Cole/Destin  |
| Transfers           | Cole/Destin  |
| Balances           | Rana/Nathan  |
| Timeout            | Rana/Nathan  |
| Error messages     | Rana/Nathan  |
| Cancelling         | Rana/Nathan  |
| Logs               | Rana/Nathan  |
| Receipts           | Rana/Nathan  |

### 2.3.2 When Will testing Occur?

Exploratory testing will begin when the testers have verified the following:

- The environment is setup to run the system
- The high-level testing plan is built
- There are at least 2 group members available for pair testing

Exploratory testing will be conducted for no more than 30 minutes by each pair of testers.

# 3 Comparison of exploratory and manual functional testing

Exploratory testing provides the tester freedom to explore the software through their own intuition and perspective. By creating a test plan to help guide the exploratory testing, we were still able to uncover multiple bugs and cover most of the app’s core functionality. For example, exploratory testing identified critical defects like the incorrect dispensing of money when inquiring about a balance. It also caught deposit-related issues, such as discrepancies in the deposited balances, and transfer-related issues, including inaccurate amounts and unexpected behavior. Another example would be receipt-related issues, such as misplacing the account details for transfers on the receipt, specifically, flipping the "transferred from" and "transferred to" accounts.

A total of 10 major bugs were identified through exploratory testing. On the downside, it is difficult to have repeatability with exploratory testing since there is no predefined script to follow. There is no guarantee that the same bugs would be identified in another iteration of exploratory testing. Due to the lack of repeatability, exploratory testing is not suited for ensuring consistency in performance across software versions. 

Manual functional testing involves the tester following a set of scripted tests. These tests can cover most functionalities and can be repeated after any changes to the software are made. Since they are scripted, they can generally be completed within a known time limit and by testers with less experience. Over multiple test cycles, manual functional testing becomes more efficient. The repeatable nature of scripted tests makes them well-suited for re-testing new software releases.

During manual functional testing, no new defects were identified for deposits or transfers, confirming the bugs previously found during exploratory testing. They did however uncover five edge-case bugs in other areas that were missed by exploratory testing. Performing MFT ensured all functionalities were thoroughly checked and validated, especially edge cases.

In practice, a testing plan that includes both methods is the most robust. Exploratory testing can help identify new or unique bugs, while manual functional testing is useful for the validation of core features and for ensuring consistency in performance across versions. Exploratory testing was effective in identifying standout bugs early, while manual functional testing revealed less obvious bugs and ensured consistent verification of all functionalities.


# 4 Notes and discussion of the peer reviews of defect reports

Some of the team’s key considerations when peer reviewing the defect reports were as follows:
- Maintaining consistency across priority ratings: The definitions of “Low”, “Medium”, and “Critical” priority are not inherently obvious, and it was important that the team was using a consistent rating scale so that bug defects could be addressed in an appropriate order.
- Ensuring thoroughness in reports: It is important that every bug report is detailed enough to understand and recreate the bug whether or not the reviewer has experienced it. When reviewing reports, the reviewer ensured that they could follow the reports and recreate the bugs.

Overall, the peer review process was well-received and had a positive impact on the quality and consistency of the defect reports. As the system complexity increases, the value of peer reviews would also increase.

# 5 How the pair testing was managed and team work/effort was divided 

As a team of four, we first split into two pairs. Each pair was assigned roughly half of the testing scope, based on the SUT’s key functionalities. The pair assigned to each scope is included in section 2.3.1. We completed pair testing, where one member conducts the tests and the other reviews and documents the test. Each member completed half of their tests as the tester, and the other half as the reviewer.

When reviewing reports, all team members reviewed all other reports that they did not write themselves.

The lab report was written as a team in Google Docs and then transferred to markdown format once complete to enable easier collaboration.

# 6 Difficulties encountered, challenges overcome, and lessons learned

The first challenge we encountered involved setting up the Jira Kanban board for bug tracking. To maintain consistent bug reports adhering to the assignment guidelines, we decided to create a custom issue template. After adding and removing custom fields, we found that many of the unused fields were being printed when exporting to .docx or .csv. To resolve this, we manually removed empty fields from the .docx export.

We also encountered some challenges relating to team coordination when reporting bugs during the exploratory testing phase. The flexible nature of exploratory testing led to multiple team members identifying and reporting some of the same bugs when both pairs were working simultaneously. To resolve this, we created an internal Google sheets tracker that provided a live status on which pair was reporting which bugs.

A lesson learned during this assignment was the value of creating scripted tests to enable regression testing. In typical classroom settings, we do not work with multiple versions of the same software, so there has not been a need for regression testing. By testing V1.0 and V1.1 of the same ATM software, having a set of scripted tests was useful to observe fixes and find newly created bugs.

# 7 Comments/feedback on the lab and lab document itself

This lab provided some useful exposure to software testing and introduced some techniques that are used in industry. We were happy to work with Jira to track bug reports and enjoyed experimenting with the pair testing approach.

Overall, we appreciated the level of detail in the lab document. However, it was not fully clear on the desired scope of the testing plan for the exploratory testing. We limited our plan to include test type, scope, and logistics to stay explicitly consistent with the rubric, but the requirements could have been more clear in the lab description.
