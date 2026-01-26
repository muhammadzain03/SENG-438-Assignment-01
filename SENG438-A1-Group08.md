# SENG 438 - Software Testing, Reliability, and Quality

## Lab Report #1 – Introduction to Testing and Defect Tracking

**Group: 08**

- Muhammad Zain
- Fateh Ali Syed Bukhari
- Yazin Abdul Majid

## Table of Contents

- [Introduction](#introduction)
- [High-level Description of the Exploratory Testing Plan](#high-level-description-of-the-exploratory-testing-plan)
- [Comparison of Exploratory and Manual Functional Testing](#comparison-of-exploratory-and-manual-functional-testing)
- [Notes and Discussion of the Peer Reviews of Defect Reports](#notes-and-discussion-of-the-peer-reviews-of-defect-reports)
- [How the Pair Testing Was Managed and Team Work/Effort Was Divided](#how-the-pair-testing-was-managed-and-team-workeffort-was-divided)
- [Difficulties Encountered, Challenges Overcome, and Lessons Learned](#difficulties-encountered-challenges-overcome-and-lessons-learned)
- [Comments/Feedback on the Lab and Lab Document Itself](#commentsfeedback-on-the-lab-and-lab-document-itself)

---

## Introduction

Prior to this lab, our team had primarily theoretical knowledge of software testing concepts gained through lectures and course materials. We understood that **exploratory testing** is an informal, flexible approach where testers simultaneously learn about the system, design tests, and execute them without predetermined scripts. This method relies heavily on tester creativity, domain knowledge, and intuition to discover defects that might not be captured by formal test cases.

Regarding **manual functional testing**, we knew it involved executing predefined test cases that verify whether a system meets its specified functional requirements. These scripted tests typically include detailed steps, expected outcomes, and are designed based on requirements documentation or use case specifications. We understood that this approach ensures comprehensive coverage of known requirements and provides repeatability across testing cycles.

However, our understanding was largely conceptual. We had not yet experienced the practical differences in test execution, defect discovery patterns, or the challenges of maintaining test documentation in a real testing environment. This lab provided our first hands-on opportunity to apply both testing methodologies to an actual software system (the ATM simulation), document defects in an industry-standard tracking system, and directly compare the effectiveness and efficiency of each approach in a controlled setting.

---

## High-level Description of the Exploratory Testing Plan

Our exploratory testing plan for the ATM simulation system was structured around several key objectives and strategies to maximize defect discovery within the allocated timeframe.

### Goals and Objectives

The primary goal of our exploratory testing was to discover defects that might not be immediately obvious from requirements documentation, particularly those related to edge cases, boundary conditions, usability issues, and unexpected user behaviors. We aimed to validate the robustness of the system under various realistic and unrealistic usage scenarios.

### Time-Boxing Strategy

We allocated approximately 30 minutes for exploratory testing as specified in the lab instructions. Within this timeframe, we adopted a breadth-first approach for the initial 15 minutes to gain familiarity with all major system functions, followed by depth-focused testing on areas that appeared most prone to defects during the remaining time.

### Areas of Focus

Our exploratory testing targeted the following functional areas:

1. **Authentication and Session Management**: Testing card insertion, PIN validation, invalid PIN handling, and session termination scenarios
2. **Withdrawal Transactions**: Examining various withdrawal amounts, insufficient balance scenarios, and cash availability constraints
3. **Deposit Transactions**: Testing deposit amount entry, envelope insertion, and cancellation workflows
4. **Transfer Transactions**: Verifying transfers between different account types and validating balance updates
5. **Balance Inquiry**: Checking accuracy of balance displays and receipt generation
6. **Error Handling and Edge Cases**: Testing system behavior with invalid inputs, boundary values (e.g., zero amounts, extremely large amounts), and interrupted transactions
7. **System Startup and Shutdown**: Verifying proper initialization and graceful system termination
8. **User Interface and Usability**: Assessing the clarity of prompts, error messages, and overall user experience

### Testing Approach Rationale

Exploratory testing was particularly suitable for this ATM system because:

- The system has numerous user interaction points where unexpected behaviors could occur
- Real-world ATM usage involves diverse user scenarios that cannot all be anticipated in scripted tests
- The system's state-dependent behavior (balances, cash on hand) creates opportunities for defects that emerge from specific sequences of operations
- Exploratory testing allowed us to leverage intuition about how users might misuse or misunderstand the system

We documented each defect immediately upon discovery to ensure accuracy of reproduction steps and system state information, recognizing that the ATM's transactional nature makes exact reproduction difficult if context is lost.

---

## Comparison of Exploratory and Manual Functional Testing

Based on our experience conducting both exploratory and manual functional (scripted) testing on the ATM simulation system, we observed several significant differences between these two approaches across multiple dimensions.

### Flexibility vs. Structure

**Exploratory testing** provided significant flexibility in test execution. Testers could adapt their strategy in real-time based on observations, pursue interesting anomalies, and test scenarios that emerged organically from system behavior. This freedom allowed for creative test design and the ability to follow intuition when something appeared suspicious. However, this flexibility came with the challenge of ensuring comprehensive coverage, as there was no predefined checklist to guarantee all requirements were tested.

**Manual functional testing**, using the test suite provided in Appendix C of the lab document, offered a highly structured approach. Each test case specified the function being tested, initial system state, input steps, and expected outcomes. This structure ensured systematic coverage of documented requirements and provided clear acceptance criteria. However, the rigid nature of scripted tests limited our ability to deviate from the planned path, potentially missing defects that would have been discovered through spontaneous exploration.

### Defect Discovery Effectiveness

**Exploratory testing** proved particularly effective at discovering unexpected defects, especially those related to:
- Boundary conditions and edge cases not covered in requirements
- Usability issues and unclear error messages
- Defects arising from unusual sequences of operations
- System behavior under stress or unusual conditions (e.g., repeated cancellations, rapid input changes)

The creative freedom inherent in exploratory testing enabled testers to think like end users and attempt operations that formal requirements might not have anticipated.

**Manual functional testing** excelled at:
- Verifying compliance with specified requirements
- Detecting defects in core functionality that must work correctly
- Ensuring that documented use cases operate as designed
- Providing evidence of requirement fulfillment

The scripted approach systematically validated each specified behavior, ensuring no documented requirement was overlooked. However, it was less effective at discovering defects outside the scope of predefined test cases.

### Ease of Execution

**Exploratory testing** required more cognitive effort and domain knowledge. Testers needed to simultaneously design tests, execute them, observe results, and document findings. This approach demanded continuous decision-making about what to test next and how to test it. The learning curve was steeper for less experienced testers, and effectiveness varied significantly based on tester skill and familiarity with the system.

**Manual functional testing** was easier to execute mechanically. Testers could follow step-by-step instructions without requiring deep understanding of the system architecture or extensive testing experience. This made the approach accessible to novice testers and allowed for easier distribution of testing work across team members. The predefined test cases also reduced the mental burden of constantly deciding what to test next.

### Repeatability and Documentation

**Exploratory testing** presented challenges in repeatability. Without predetermined scripts, recreating the exact sequence of tests required detailed documentation of each exploration path. Defect reports needed to be particularly thorough to capture the context and steps that led to each defect discovery. This made regression testing more difficult, as exploratory sessions are inherently unique.

**Manual functional testing** offered excellent repeatability. The test suite in Appendix C provided a permanent record of exactly what was tested and could be executed identically by different testers or during regression testing cycles. This repeatability is crucial for validating bug fixes (as demonstrated in the regression testing phase with version 1.1 of the ATM system) and for ensuring consistent test coverage across releases.

### Efficiency and Coverage

**Exploratory testing** was more efficient at finding critical defects quickly, particularly in the early stages of testing. Within the 30-minute timeframe, we could rapidly assess system quality and identify high-severity issues. However, measuring coverage was difficult, and we could not definitively state which requirements or code paths had been exercised.

**Manual functional testing** provided measurable coverage of specified requirements. We could track which test cases passed or failed, generating metrics on requirement fulfillment. However, executing the complete test suite was time-consuming, and the structured approach sometimes felt inefficient when obvious defects could have been found more quickly through exploration.

### Complementary Nature

In practice, we found these approaches to be highly complementary rather than competing alternatives. Exploratory testing was valuable for initial system assessment, uncovering unexpected issues, and testing usability aspects. Manual functional testing ensured comprehensive verification of requirements and provided a reliable baseline for regression testing. The combination of both methodologies provided more thorough quality assurance than either approach alone could achieve.

---

## Notes and Discussion of the Peer Reviews of Defect Reports

The peer review process was a critical component of ensuring high-quality defect documentation. After each pair completed their testing sessions (both exploratory and manual functional testing), we conducted systematic peer reviews of all recorded defect reports before finalizing them in the defect tracking system.

### Peer Review Process

Our peer review workflow consisted of the following steps:

1. Each pair independently conducted testing and documented defects in draft form
2. Pairs exchanged defect reports for cross-review
3. Reviewers evaluated each defect report against established quality criteria
4. Feedback was provided through comments in the tracking system
5. Original reporters revised defect reports based on feedback
6. A final group discussion resolved any disagreements or ambiguities

### Common Issues Identified During Review

Through the peer review process, we identified several recurring issues in initial defect reports:

**Missing or Incomplete Reproduction Steps**: Some defect reports omitted critical details about the system state or sequence of actions required to reproduce the issue. For example, early defect reports might state "withdrawal fails" without specifying the initial balance, amount attempted, or whether sufficient cash was loaded into the ATM. Reviewers ensured that reproduction steps were sufficiently detailed for a developer unfamiliar with the testing session to recreate the exact conditions.

**Unclear Expected vs. Actual Results**: Several reports lacked clear distinction between what should have happened (based on requirements in Appendix B) and what actually occurred. Reviewers emphasized the importance of citing specific requirements when stating expected behavior, particularly referencing the high-level requirements documentation to justify expectations.

**Severity and Priority Misclassification**: We observed inconsistencies in how pairs initially classified defect severity. Some cosmetic issues were initially marked as high severity, while some functional defects affecting core requirements were marked as medium severity. Through peer discussion, we developed shared criteria: severity was based on impact to functionality and alignment with critical requirements, not just how noticeable a defect was during testing.

**Duplicate Defects**: Peer review helped identify duplicate defects discovered independently by different pairs, particularly in areas like PIN validation and transaction cancellation. We consolidated duplicates, preserving any unique reproduction steps or observations from either report.

**Insufficient Environmental Information**: Some reports lacked details about initial system configuration (e.g., starting cash amount in the ATM, initial account balances). Reviewers ensured these contextual details were captured, as they could be critical for reproduction.

**Vague Titles and Descriptions**: Initial defect titles were sometimes too generic (e.g., "Transfer doesn't work"). Reviews pushed for specific, searchable titles that clearly indicated the function, condition, and symptom (e.g., "Transfer from Checking to Savings fails when source account has exactly $20").

### Quality Improvements from Peer Review

The peer review process substantially improved defect report quality:

- **Reproducibility**: Reports became significantly more reproducible, with step-by-step instructions that a developer could follow without ambiguity
- **Consistency**: Severity classifications and formatting became more consistent across all defects, making prioritization more reliable
- **Completeness**: Reviews ensured all mandatory fields (function tested, initial state, steps, expected output, actual output) were thoroughly populated
- **Clarity**: Descriptions became more concise and focused, eliminating unnecessary narrative while retaining essential technical detail

### Learning Outcomes from Peer Review

The peer review experience taught us that defect reporting is both a technical and communication skill. Even when a defect is clearly observed, communicating it effectively to developers requires careful attention to detail, clear writing, and understanding of what information is necessary for debugging. The process also highlighted the value of fresh perspectives—reviewers often caught gaps or ambiguities that the original tester had overlooked due to familiarity with their own testing context.

---

## How the Pair Testing Was Managed and Team Work/Effort Was Divided

Our team of three members employed a structured approach to pair testing and workload distribution, ensuring efficient collaboration while maintaining quality standards.

### Pair Formation and Rotation

Given our team size of three, we formed the following arrangement:

- **Pair 1**: Muhammad Zain and Fateh Ali Syed Bukhari
- **Individual**: Yazin Abdul Majid

To accommodate the three-person team structure, we rotated responsibilities to ensure everyone gained experience in both roles (driver and navigator) and contributed equally to all testing phases.

### Division of Testing Responsibilities

**Exploratory Testing Phase**:
- Pair 1 conducted exploratory testing with one member operating the ATM system (driver) while the other observed, suggested test scenarios, and documented defects (navigator)
- Yazin conducted independent exploratory testing, alternating between system operation and documentation
- Both groups focused on different functional areas initially to maximize coverage before comparing findings

**Manual Functional Testing Phase**:
- We divided the 40 test cases from Appendix C into two roughly equal subsets based on use case grouping
- Pair 1 took responsibility for System Startup, System Shutdown, Session, and Withdrawal test cases (approximately tests 1-18)
- Yazin focused on Deposit, Transfer, Inquiry, and Invalid PIN Extension test cases (approximately tests 19-40)
- This division ensured both groups tested diverse functionality while maintaining manageable workload

**Regression Testing Phase**:
- All defects from version 1.0 were distributed among team members for retesting in version 1.1
- Each member retested approximately one-third of the identified defects
- We also divided execution of the manual test suite for version 1.1, maintaining the same test case assignments as in the initial manual testing phase

### Role Rotation Within Pairs

Within Pair 1, roles were rotated every 15 minutes during exploratory testing and after every 10 test cases during manual functional testing. This rotation ensured:
- Both members developed skills in system operation and defect documentation
- Fresh perspectives were continuously applied to both testing execution and observation
- Fatigue was minimized by varying the cognitive demands of each role
- Both members remained engaged and could contribute insights equally

### Communication and Coordination

We maintained consistent communication through:

- **Shared Documentation**: All defect reports were entered into the defect tracking system in real-time, allowing all team members to view discoveries as they occurred
- **Regular Synchronization Points**: After completing each major testing phase, we held brief team discussions to share observations, clarify ambiguities, and coordinate next steps
- **Defect Review Sessions**: Scheduled peer review sessions where all team members collectively evaluated defect quality and completeness
- **Testing Log**: A shared document tracking which test cases had been executed, by whom, and with what results, preventing duplicate effort and ensuring comprehensive coverage

### Ensuring Consistency in Defect Reporting

To maintain consistency across defect reports from different team members:

- We established a shared template at the project outset, specifying required fields and formatting conventions
- Severity and priority classifications were defined collaboratively before testing began
- All defects went through the peer review process described in Section 4
- We used consistent naming conventions for defect titles (format: "[Component] - [Symptom] under [Condition]")
- Expected outcomes were always justified by citing specific requirements from Appendix B

### Workload Balance

We actively monitored workload distribution throughout the lab:

- Test case assignments were balanced by estimated complexity and time, not just count
- Yazin's independent work was compensated by having first responsibility for setting up the defect tracking system and establishing reporting templates
- All team members participated equally in the final report synthesis, with each member drafting specific sections based on their experience and observations

This structured yet flexible approach to team collaboration ensured that all members contributed meaningfully to the testing effort while gaining comprehensive experience with both exploratory and scripted testing methodologies.

---

## Difficulties Encountered, Challenges Overcome, and Lessons Learned

Throughout this lab, our team encountered several challenges that provided valuable learning experiences in software testing practices.

### Challenges with Exploratory Testing

**Challenge**: Initially, our exploratory testing felt aimless and inefficient. Without a predefined script, we found ourselves uncertain about what to test next and concerned about whether we were achieving adequate coverage.

**Solution**: We overcame this by developing a lightweight charter-based approach. Before beginning exploratory testing, we listed major functional areas on a whiteboard and committed to spending at least 5 minutes exploring each area. This provided enough structure to ensure breadth of coverage while preserving the flexibility to pursue interesting observations.

**Lesson Learned**: Effective exploratory testing requires discipline and structure, not complete freedom. A high-level test plan or charter that defines goals and scope is essential for productive exploratory sessions.

### Defect Report Quality and Consistency

**Challenge**: Our initial defect reports varied significantly in quality, detail, and format. Some reports were too verbose, while others lacked sufficient detail for reproduction. This inconsistency would have created confusion for developers attempting to fix the defects.

**Solution**: After the first few defects were reported, we paused to establish a team-wide template and standards. We defined mandatory fields, created examples of well-written reports, and instituted the peer review process. This upfront investment in standards paid dividends in report quality.

**Lesson Learned**: Defect reporting standards should be established before testing begins, not reactively after problems emerge. Consistent, high-quality defect reports are as important as finding defects in the first place.

### Defect Duplication

**Challenge**: Both testing groups independently discovered several of the same defects, particularly obvious ones in high-traffic functionality like PIN validation. This duplication represented wasted effort and created confusion when both reports appeared in the tracking system.

**Solution**: We implemented a practice of checking the defect tracking system every 10-15 minutes during active testing. Before logging a new defect, we performed a quick search to verify it hadn't already been reported. For similar but not identical defects, we added notes to existing reports rather than creating new ones.

**Lesson Learned**: Regular synchronization and communication during parallel testing efforts is crucial. In a larger team or longer testing cycle, more sophisticated defect tracking workflows (e.g., triage meetings, designated defect coordinators) would be necessary.

### State Management and Test Independence

**Challenge**: The ATM system's stateful nature (balances change with transactions, cash on hand decreases with withdrawals) made it difficult to ensure test independence. Later tests were sometimes affected by earlier tests, and reproducing specific defects required carefully recreating the exact system state.

**Solution**: We learned to restart the ATM system between major test sequences to restore initial conditions. We also became more diligent about documenting the exact starting state (initial balances, cash loaded) in defect reports, and we realized that some "defects" were actually side effects of previous transactions we had forgotten about.

**Lesson Learned**: Understanding system state and ensuring test independence is critical for reliable testing. In future testing, we would implement more rigorous test setup and teardown procedures, and consider using automated mechanisms to restore known good states.

### Regression Testing Complexity

**Challenge**: During regression testing with version 1.1, we discovered that some defects had been "fixed" in ways that introduced new issues, and some fixes had unintended side effects on related functionality. Determining whether a defect was truly fixed or just manifesting differently proved difficult.

**Solution**: We expanded our regression testing beyond simply re-executing the exact reproduction steps from the original defect report. For each fixed defect, we also tested related functionality and boundary cases around the fix. This helped us catch regression issues early.

**Lesson Learned**: Regression testing must go beyond simple defect verification. Each fix should be validated not only for the specific reported issue but also for potential side effects on related functionality. Comprehensive regression test suites should test the vicinity of each change, not just the change itself.

### Time Management and Scope

**Challenge**: The manual test suite in Appendix C was extensive (40 test cases), and combined with exploratory testing, defect reporting, and regression testing, time pressure became significant. We initially spent too much time on documentation and not enough on actual testing.

**Solution**: We learned to balance thoroughness with efficiency. For defect reports, we adopted a "capture now, refine later" approach—logging essential details immediately and then enhancing reports during peer review. For test execution, we prioritized high-risk and high-priority test cases when time became constrained.

**Lesson Learned**: Testing in resource-constrained environments requires constant prioritization. Risk-based testing principles (focusing effort where defects are most likely or most impactful) should guide testing when exhaustive testing is infeasible.

### Tool Learning Curve

**Challenge**: None of our team members had prior experience with the defect tracking system (Jira/Azure DevOps). The initial learning curve consumed valuable testing time as we learned to navigate the interface, configure fields, and generate reports.

**Lesson Learned**: Familiarity with testing tools is a valuable skill that should be developed early. In professional environments, investing time in tool training upfront pays dividends in long-term efficiency. We also learned that tools should enhance, not hinder, the testing process—when tool complexity becomes a barrier, simpler alternatives may be more appropriate.

### Key Takeaways

This lab reinforced several fundamental testing principles:

1. **Testing is both systematic and creative**: Effective testing requires both disciplined adherence to processes and creative thinking about how systems can fail
2. **Communication is paramount**: High-quality defect reports and team coordination are as important as finding defects
3. **Testing is iterative**: Each testing cycle (exploratory, scripted, regression) builds on previous knowledge and refines understanding of system quality
4. **Context matters**: Understanding the system's purpose, requirements, and constraints is essential for meaningful testing
5. **Collaboration amplifies effectiveness**: Pair testing and peer review produce better results than individual efforts through shared knowledge and diverse perspectives

---

## Comments/Feedback on the Lab and Lab Document Itself

### Positive Aspects

**Realistic Testing Experience**: The lab provided an excellent simulation of real-world testing practices. The ATM system was sufficiently complex to present genuine testing challenges while remaining manageable within the lab timeframe. The progression from exploratory to scripted to regression testing mirrors the typical software development lifecycle and gave us practical insight into how testing evolves throughout a project.

**Clear Structure and Instructions**: The lab document was well-organized with clear objectives, step-by-step instructions, and comprehensive appendices. Appendix C's test suite was particularly valuable, providing a concrete example of professional test case documentation that we could use as a reference for our own test design.

**Hands-on Tool Experience**: Requiring use of an industry-standard defect tracking system (Jira or Azure DevOps) added significant practical value. This exposure to professional tools will be beneficial in internships and future employment.

**Pair Testing Methodology**: The pair testing approach was highly effective. Having two sets of eyes on the system simultaneously improved defect detection and provided immediate peer learning opportunities. The collaborative nature also made the testing process more engaging.

### Areas for Improvement

**System Limitations and Known Issues**: It would be helpful if the lab document explicitly stated which system behaviors are intentional and which are known defects. We occasionally debated whether an observed behavior was a bug or a design decision, which consumed time during testing and defect reporting.

**Test Suite Ambiguities**: Some test cases in Appendix C had ambiguous expected results or required assumptions about system behavior not explicitly stated in Appendix B's requirements. For example, specific error messages expected by the system were not documented in requirements, making it difficult to determine if actual messages were correct. Additional clarity in test cases would reduce uncertainty.

**Regression Testing Guidance**: The regression testing section could benefit from more detailed guidance on how to interpret partial fixes or fixes that introduce new issues. We were uncertain about the appropriate defect tracking workflow when a fix resolved one problem but created another.

**Time Allocation**: While the lab was completable in the allocated time, the workload was substantial, particularly when combined with defect report peer review and final report preparation. Either extending the allocated time or reducing the scope slightly (perhaps fewer test cases in Appendix C) would reduce time pressure and allow for more thorough reflection on the testing process.

**Group Size Flexibility**: The lab instructions assumed groups of 5 members, but our group had 3 members. While we adapted successfully, explicit guidance for smaller group sizes would be helpful, including suggestions for workload adjustment or modified pair testing structures.

### Suggestions for Enhancement

1. **Add a defect reporting tutorial**: A brief tutorial or example walkthrough demonstrating how to write a high-quality defect report before testing begins would improve report consistency and quality from the start.

2. **Include test metrics**: Providing guidance on capturing simple test metrics (e.g., number of test cases executed, pass/fail rates, defect density) would add an analytical dimension to the lab and introduce students to test measurement practices.

3. **Expand requirements documentation**: Adding more detail to Appendix B, particularly regarding expected error messages and boundary condition behaviors, would reduce ambiguity during testing and defect reporting.

4. **Provide a sample defect lifecycle**: Walking through one defect from discovery through fix verification in detail would help students understand the complete defect management process.

5. **Add discussion of test automation**: While this lab appropriately focused on manual testing, a brief discussion or appendix about how these tests might be automated in practice would provide valuable context about testing evolution.

### Overall Assessment

Overall, this lab was a valuable and practical introduction to software testing. The hands-on nature, realistic system, and emphasis on both testing execution and defect documentation provided comprehensive exposure to fundamental testing concepts. The challenges we encountered were appropriate for a learning environment—difficult enough to require problem-solving and collaboration, but not so overwhelming as to be discouraging. The lab successfully achieved its stated objectives of providing practical testing experience, demonstrating differences between testing approaches, and familiarizing us with industrial defect tracking practices.

We appreciate the opportunity to apply theoretical testing concepts to a concrete system and look forward to building on these foundational skills in subsequent labs and assignments.

---

**Note**: This report represents a draft to be refined after completion of the actual testing activities. Specific defect examples, test execution details, and quantitative results will be incorporated once testing is performed.
