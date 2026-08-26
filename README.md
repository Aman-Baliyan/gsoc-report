
# Google Summer of Code 2026 Final Report



### **Project**: [Open JDK Code convention coverage](https://github.com/checkstyle/checkstyle/wiki/Checkstyle-GSoC-2026-Project-Ideas#project-name-open-jdk-code-convention-coverage)



### **Student**: [Aman Baliyan](https://github.com/Aman-Baliyan)



### **Organization**: [Checkstyle](https://github.com/checkstyle)



### **Mentors**: [Roman Ivanov](https://github.com/romani), [Baratali Izmailov](https://github.com/baratali)



### **GSoC Proposal**: [here](https://github.com/Aman-Baliyan/gsoc-report/blob/main/Proposal%20for%20openjdk-style-guide.pdf)



---

### Project Goals

The project aims to complete Checkstyle coverage for the [New_OpenJDK_Java_Style_Guidelines](https://cr.openjdk.org/~alundblad/styleguide/index-v6.html) and the existing [Old_OpenJDK_Style_guide](https://www.oracle.com/java/technologies/javase/codeconventions-contents.html). The goal is to complete the coverage report, add all applicable checks to [openjdk_checks.xml](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/openjdk_checks.xml), and update the existing [sun_checks.xml](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/sun_checks.xml) configuration. Where required functionality is missing, new Checkstyle modules will be implemented or existing checks will be enhanced with new properties. The project also includes adding and updating tests to validate the covered guidelines and updating the corresponding coverage documentation to provide a clear mapping between the style guide rules and Checkstyle implementations.

---



### What I Did During GSoC



1.  **Added Two Comment Triggers for Report Generation**: Added two new PR comment triggers to the existing GitHub Actions workflow for automated report generation:

- **Diff Report:** Added a trigger to generate a diff report when a new Checkstyle check is added to a style configuration file. This helps identify the changes in violations and coverage introduced by the newly added check.

- **Complete Base Report:** Added a trigger to generate a complete base report for an entire style configuration file against any target project. This provides a complete overview of the current violations and serves as a baseline for further analysis.

**PRs:**
- Diff Report Trigger: https://github.com/checkstyle/checkstyle/pull/19982
- Complete Base Report Trigger: https://github.com/checkstyle/checkstyle/pull/20255

2.  **Updated OpenJDK Style Guide Tests and Coverage**: Reviewed the OpenJDK Style Guide in detail and updated its Checkstyle coverage by identifying the corresponding Checkstyle checks for each applicable guideline. Added the relevant existing checks to the style guide coverage in [#19798](https://github.com/checkstyle/checkstyle/issues/19798) and created new tests to verify their behaviour against the documented rules. Where a guideline was not covered by an existing Checkstyle check, investigated the missing functionality, created dedicated issues to track the required implementation, and referenced those issues in the coverage documentation.  Also added and updated tests to ensure that the covered guidelines are properly validated, resulting in a more complete and accurate representation of OpenJDK Style Guide support in Checkstyle. The coverage report is [here](https://checkstyle.sourceforge.io/openjdk_style.html).

3.  **Implemented New Checks and Check Properties**: Implemented new Checkstyle modules for OpenJDK Style Guide rules that were not supported by the existing checks. Also enhanced existing checks by introducing new properties where the current functionality was insufficient to enforce specific OpenJDK guidelines. These changes extend Checkstyle's capabilities and allow the style guide coverage to be mapped more accurately to the corresponding validation rules.
New checks added are - [OpenjdkAnnotationLocation](https://checkstyle.org/checks/annotation/openjdkannotationlocation.html#OpenjdkAnnotationLocation)
[PreferLiteralJavadocInlineTag](https://checkstyle.org/checks/javadoc/preferliteraljavadocinlinetag.html#PreferLiteralJavadocInlineTag)
[PreferCodeOrSnippetJavadocInlineTag](https://github.com/checkstyle/checkstyle/issues/20986)



---

### Current Status and Future Work

The project is currently in a stable state, with the majority of the planned work successfully completed. The new OpenJDK Style Guide has been extensively reviewed, its coverage has been updated, and most of the required modules have been implemented. 

However, there are still several areas that require further work and can be addressed as future enhancements:

- **Remaining Modules**: A few modules required for complete coverage of the new OpenJDK Style Guide are still pending. These are documented in the [OpenJDK Style Guide coverage page](https://checkstyle.sourceforge.io/openjdk_style.html) and can be implemented in future work.

- **Sun Style Guide Coverage**: Updated the tests for the existing old OpenJDK (Sun) Style Guide coverage and created [#20811](https://github.com/checkstyle/checkstyle/issues/20811) to track the remaining work required to complete its coverage. The issue covers reviewing the [Sun Code Conventions](https://www.oracle.com/java/technologies/javase/codeconventions-contents.html), identifying the guidelines that are not yet covered, and implementing the required changes to achieve complete coverage of the existing OpenJDK/Sun Style Guide.


---

### Code Contributions

- All PRs/Issues related to the project can be found in [GitHub project board](https://github.com/orgs/checkstyle/projects/16).

- All PRs related to coverage of new openjdk style guide are [here](https://github.com/checkstyle/checkstyle/issues/19798).

- Pr related to github actions are - [#19982](https://github.com/checkstyle/checkstyle/pull/19982), [#20255](https://github.com/checkstyle/checkstyle/pull/20255)

- All my contributions to checkstyle can be found [here](https://github.com/checkstyle/checkstyle/commits?author=Aman-Baliyan).
- All issues opened by me can be found [here](https://github.com/checkstyle/checkstyle/issues/created_by/Aman-Baliyan?q=is%3Aissue%20author%3AAman-Baliyan).


---



### What I Learned During GSoC



#### Technical Skills:

- **Implementing new Checks/Features**: While working on this project, based on new rules I had implement new Checks and Features to extend our coverage. Implementing such features have helped me to improve my problem solving ability, it forced me to find a way to solve the problem in an effective and efficient way. Implementing new Checks & Features helped to understand how Checkstyle works at it core and how the Checkstyle API works under the hood.

-  **Bug Solving**: I have developed a good skill of bug solving by finding and solving many bugs in Checkstyle Checks. I required to work on many Checks as part of this project, I had to go through different types of Check's implementation written by someone else in the past and find a way to fix the Check's implementation to reduce the number of false-positives/negatives. This has helped me to understand code written by other contributors and improve the code quality.

-  **Code Quality**: Working on Checkstyle has improved my ability to write clean and optimized code by enforcing high coding standards. Checkstyle uses JaCoCo for code coverage metrics, it follows a strict policy of 100% code coverage. Checkstyle uses PIT for mutation testing, following such standards have helped me to develop a habit of writing more efficient and maintainable code while following a good coding style.


#### Non-Technical Skills:

- **Project Management**: The project was divided into two major phases to ensure a structured and efficient implementation. The first half focused on reviewing the OpenJDK Style Guide, updating the coverage report, and creating and updating tests to establish a complete understanding of the existing coverage and identify missing functionality. The second half focused on implementing the missing modules and enhancing existing checks with new properties where required. While working on these tasks, several defects and gaps in the existing implementation were identified. My mentors and I discussed these issues, divided them into smaller tasks, and prioritized them based on their impact. This structured approach helped me manage the project effectively and gave me a better understanding of how large open-source projects are planned, prioritized, and developed collaboratively.

-  **Effective Communication**: Though English is my second language I got to communicate with my experienced mentors and it has improved my communication skills by a great factor. I learnt how to effectively communicate with mentors and handle disagreements. By communicating with them, I learnt a lot about how we can solve a complex problem by collaborating with other team members, how to ask good questions and understand other person's opinion.

- **Teamwork and Collaboration**: Working with my mentors taught me the value of teamwork. We often brainstormed ideas, discussed potential solutions to problems, and shared feedback on each other's work. I learned to appreciate the different perspectives each team member brought to the table and how to work efficiently in a team, especially when dealing with a large codebase and complex issues. This experience has significantly enhanced my ability to work in collaborative environments and be more adaptable in future projects.

Overall, This experience has been incredibly enriching, both technically and personally. I’ve gained valuable skills in project management, communication, and teamwork, along with a deeper understanding of how large open-source projects are maintained. These lessons have boosted my confidence and will serve as a strong foundation for my future career in software development.

---



### Acknowledgements

I would like to express my deepest gratitude to my mentor, [Roman Ivanov](https://github.com/romani) for his unwavering support and guidance throughout this project. His calm and understanding nature made it easy for me to ask questions, I got to learn so much from their experience. I also want to thank [Mohit Sharma](https://github.com/mohitsatr), who was always willing to help and provided detailed explanations to clear my doubts. This project would not have been possible without their invaluable mentorship and assistance. I am looking forward to keep contributing to Checkstyle and help other new comers to get their open-source journey started.
