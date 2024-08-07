+++
author = "dev@cyber200"
title = "Mitigation and Verification"
date = "2024-08-06"
description = ""
tags = [
    "cyber-security",
    "web-app-security",
    "mitigation-and-verification",
]
draft = false
+++

### Improve Security Posture

#### Software Development Life Cycle (SDLC)
- The requirement phase is used to capture all requirements from the customer and create the proper documentation.
- The design phase is where members from different departments will meet and talk/design how they will implement the requirements.
- The development phase is where the development team actually do all coding.
- The testing phase is where the QA team tests what was committed by the developer.
- Code is released but continuously maintained or improved by the development team.

#### Scenario

The company has decided the application that is being built by the team is being flagged as mission-critical. This is because there is a very high chance that the people that will hack the application will be able to do a lot of damage. Based on all this information, how to incorporate the following tasks into the SDLC based on the information above to handle the risk?

- Intel gathering->Design: 
This is the phase to offer insight on some best practices when handling certain types of data or ways to protect the application.

- SAST-> Development: This process will be incorporated into the development phase and will auto-execute every time a new commit is detected by the developer. This will create a feedback loop that will help move the security early warning closer to the developer and allow them to fix the issue before it leaves their phase.
- Penetration Testing -> QA: This process will be incorporated within the testing phase but at the end of QA testing. This helps to ensure the security testing is only done on code that is ready for production
- Verification of security fixes->Testing: This process will actually be incorporated into the testing phase but part of the QA testing process. Where QA is validating that these issues are no longer a problem based on your walk-thru. Now you will still want to verify this in your penetration testing, but having QA take a first look can help reduce cycles as they will immediately flag the issue and queue it up for development before it even gets into your backlog.

### Security Training
- Using real issues found in testing the application is the best place to start
- Gather all security issues found in our last security testing of the application, sort these items by severity and then group them by OWASP Top 10
- should do
  - Use examples that are very similar to the security issue found
  - Use the similar or same technology stack, so they are more relevant for the developers and testers.
  - Focus only on 1 topic per training
  - Setup a recurring meeting vs. ad hoc. This will make it easier for people to make time to attend.
- avoid doing
  - Calling out who introduced the security issue
  - Using code from testing that then can be linked back to the developer
  - Doing on the fly training with zero or limited agendas.

  ### Test Matrix
  A test matrix is a document that is used to capture the process of testing features within an application. The test matrix is important as they make sure all the testing is consistent and the application is working as expected. [template](https://docs.google.com/spreadsheets/d/1Ep8b2S_ELtLFaTA2q1dnm2csi0E7T4jFiIPIMwR3BaU/edit?gid=0#gid=0)

### Report Refinement
### Security Sounding Board
### Reading
- https://www.guru99.com/software-development-life-cycle-tutorial.html
- https://securityintelligence.com/need-a-sounding-board-for-your-incident-response-plan-join-a-security-community/