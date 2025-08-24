# SWE5006 Capstone Project: Kahoot Quiz  

This repository contains the capstone project for **SWE5006 - Graduate Certificate in Designing Modern Software Systems (DMSS)** at the **National University of Singapore (NUS)**.  

The project implements a **Kahoot clone**—a real-time, interactive quiz application inspired by the popular Kahoot platform. The goal is to demonstrate **modern software design principles**, **end-to-end testing**, and **CI/CD automation** with GitHub Actions and Slack integration.  

---

### Project Overview  
- Developed a **quiz application** using React, TypeScript, Vite, and Tailwind CSS.  
- Implemented **real-time quiz flow**, timer, scoring, and responsive UI.  
- Ensured correctness through **Playwright end-to-end test automation**.  
- Integrated with **GitHub Actions CI/CD pipeline** and **Slack notifications**.  


### Test Automation  

- **Framework Used:** Playwright  
- **Test Execution:** Triggered automatically via **GitHub Actions** on every push.  
- **Slack Integration:** Workflow status updates (success/failure) sent to Slack.  

#### Summary of Test Coverage  
- **Quiz Flow Tests:** Starting quiz, answering, scoring, and completion.  
- **Timer Tests:** Countdown and auto-expiry behavior.  
- **Game State Tests:** Restart quiz and sequential navigation.  
- **UI/UX Tests:** Responsiveness and feedback visuals.  
- **Edge Cases:** Rapid clicking, browser refresh reset.  
- **Data Validation:** Question integrity and score calculation.  



### Evidence of Results  

#### 📸 Screenshot 1 – Passing All Test Cases  

![alt text](<reactquitz_images/test case.png>)

#### 📸 Screenshot 2 – GitHub Actions Success  

![alt text](<reactquitz_images/Screenshot 2025-08-24 at 3.26.28 PM.png>)

#### 📸 Screenshot 3 – Slack Notification  

![alt text](<reactquitz_images/Screenshot 2025-08-24 at 2.55.45 PM.png>)

---

### Conclusion  

This practical demonstrates:  
- **Automated testing** with Playwright.  
- **Continuous Integration/Delivery (CI/CD)** using GitHub Actions.  
- **Team communication enhancement** via Slack notifications.  
- Ensured that all functional and non-functional requirements of the quiz application are verified.  

The pipeline ensures reliability, reproducibility, and real-time visibility of software quality.  

#### Github Repository 
```
https://github.com/Kinleyjigs/AS2025_SWE302_02230313_practical1.git
```
