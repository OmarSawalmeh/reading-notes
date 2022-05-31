# **Express**
<!-- ---
---

## **A.** An introduction to NodeJS.

## **B.** An introduction to Express.

## **C.** What is NPM?

## **D.** What is TDD?

## **E.** CI/CD.

---

## **A. Introducing Node:**
#### **-Node** (or more formally Node.js) is an open-source, cross-platform runtime environment that allows developers to create all kinds of server-side tools and applications in JavaScript. The runtime is intended for use outside of a browser context (i.e. running directly on a computer or server OS).

#### -From a **web server** development perspective Node has a number of benefits:
- ##### Great performance! Node was designed to optimize throughput and scalability in web applications.
- ##### Code is written in "plain old JavaScript".
- ##### The node package manager (NPM) provides access to hundreds of thousands of reusable packages.
- ##### Node.js is portable. It is available on Microsoft Windows, macOS, Linux, Solaris, FreeBSD, OpenBSD, WebOS, and NonStop OS.
- ##### It has a very active third party ecosystem and developer community.

#### **-Web Frameworks:**
#### Other common web-development tasks are not directly supported by Node itself. If you want to add specific handling for different HTTP verbs (e.g. GET, POST, DELETE, etc.), separately handle requests at different URL paths ("routes"), serve static files, or use templates to dynamically create the response, Node won't be of much use on its own. You will either need to write the code yourself, or you can avoid reinventing the wheel and use a web framework!

---
## **B. Introducing Express:**
### **-Express** is the most popular Node web framework, and is the underlying library for a number of other popular Node web frameworks. It provides mechanisms to:

### **-Express** is unopinionated. You can insert almost any compatible middleware you like into the request handling chain, in almost any order you like. You can structure the app in one file or multiple files, and using any directory structure. You may sometimes feel that you have too many choices!

### **-Helloworld Express Example**
```js
const express = require('express');
const app = express();
const port = 3000;

app.get('/', function(req, res) {
  res.send('Hello World!')
});

app.listen(port, function() {
  console.log(`Example app listening on port ${port}!`)
});
```

### **-A asynchronous VS synchronous APIs .....?????**
#### JavaScript code frequently uses asynchronous rather than synchronous APIs for operations that may take some time to complete. **[IMPORTANT NOTE]** A synchronous API is one in which each operation must complete before the next operation can start. --- **[## setTimeout() ##] EXAMPLE FOR asynchronous API**

---
## **C. npm:**
### **npm** is the world's largest software registry. Open source developers from every continent use npm to share and borrow packages, and many organizations use npm to manage private development as well.

npm consists of three distinct components:

1. the website.
2. the Command Line Interface (CLI).
3. the registry.

- Use the [website](https://www.npmjs.com/) to discover packages, set up profiles, and manage other aspects of your npm experience. For example, you can set up organizations to manage access to public or private packages.

- The [CLI](https://docs.npmjs.com/cli/v8/commands/npm) runs from a terminal, and is how most developers interact with npm.

- The [registry](https://docs.npmjs.com/cli/v8/using-npm/registry) is a large public database of JavaScript software and the meta-information surrounding it.

---
## **D. TDD:**
### **TDD** “Test-driven development” refers to a style of programming in which three activities are tightly interwoven: **coding**, **testing** (in the form of writing unit tests) and **design** (in the form of refactoring).

---
## **E. Continuous Integration(CI) Continuous Delivery(CD) [CI/CD](https://www.redhat.com/en/topics/devops/what-is-ci-cd)**
### **Overview** CI/CD is a method to frequently deliver apps to customers by introducing automation into the stages of app development. The main concepts attributed to CI/CD are continuous integration, continuous delivery, and continuous deployment. CI/CD is a solution to the problems integrating new code can cause for development and operations teams (AKA "integration hell").
### Specifically, CI/CD introduces ongoing automation and continuous monitoring throughout the lifecycle of apps, from integration and testing phases to delivery and deployment. Taken together, these connected practices are often referred to as a "CI/CD pipeline" and are supported by development and operations teams working together in an agile way with either a DevOps or site reliability engineering (SRE) approach.


- **PROBLEM AND SOLUTION USING Continuous Integration CI...** 
##### **PROBLEM** In modern application development, the goal is to have multiple developers working simultaneously on different features of the same app. However, if an organization is set up to merge all branching source code together on one day (known as “merge day”), the resulting work can be tedious, manual, and time-intensive. That’s because when a developer working in isolation makes a change to an application, there’s a chance it will conflict with different changes being simultaneously made by other developers. This problem can be further compounded if each developer has customized their own local integrated development environment (IDE), rather than the team agreeing on one cloud-based IDE.

##### **SOLUTION USING** Continuous integration (CI) helps developers merge their code changes back to a shared branch, or “trunk,” more frequently—sometimes even daily. Once a developer’s changes to an application are merged, those changes are validated by automatically building the application and running different levels of automated testing, typically unit and integration tests, to ensure the changes haven’t broken the app. This means testing everything from classes and function to the different modules that comprise the entire app. If automated testing discovers a conflict between new and existing code, CI makes it easier to fix those bugs quickly and often.

- **BENEFIT USING Continuous Delivery CD AFTER CI...** 
##### Following the automation of builds and unit and integration testing in CI, continuous delivery automates the release of that validated code to a repository. So, in order to have an effective continuous delivery process, it’s important that CI is already built into your development pipeline. The goal of continuous delivery is to have a codebase that is always ready for deployment to a production environment.In continuous delivery, every stage—from the merger of code changes to the delivery of production-ready builds—involves test automation and code release automation. At the end of that process, the operations team is able to deploy an app to production quickly and easily. -->

---
- [BACK (Main Page)](../../README.md)
---







