# 🧪 PostmanReports — API Testing Automation with GitHub Actions

This repository demonstrates **how to automate API testing using Postman and GitHub Actions**, and how to **generate beautiful HTML reports** from your test results.

It’s designed especially for **beginners** — anyone can learn how to test APIs, generate reports, and automate workflows using this project.

> 📚 Inspired and learned from [AskHerConsulting](https://github.com/AskHerConsulting)

---

## 🧭 Table of Contents

1. [Overview](#overview)
2. [What You’ll Learn](#what-youll-learn)
3. [Tools & Technologies Used](#tools--technologies-used)
4. [Project Structure](#project-structure)
5. [Step-by-Step Setup Guide](#step-by-step-setup-guide)
6. [Running Tests Locally](#running-tests-locally)
7. [Automating Tests with GitHub Actions](#automating-tests-with-github-actions)
8. [Viewing Test Reports](#viewing-test-reports)
9. [How the Collection Works](#how-the-collection-works)
10. [Learning Notes](#learning-notes)
11. [Credits](#credits)

---

## 🧩 Overview

This repository automates API testing for the **Restful Booker API**, a popular public test API used for learning and practice.

The automation uses:
- **Postman** for writing and managing API test cases.
- **Newman** (Postman’s CLI tool) for running tests automatically.
- **GitHub Actions** for continuous integration — tests run automatically whenever code is pushed.
- **HTML Extra Reporter** for generating interactive and professional-looking reports.

---

## 🎯 What You’ll Learn

Even if you have **zero experience** with Postman or GitHub Actions, this repo will teach you:

✅ How to **create and organize API test cases** in Postman  
✅ How to **export Postman collections and environments**  
✅ How to **run Postman tests using Newman (CLI)**  
✅ How to **generate HTML test reports**  
✅ How to **automate tests with GitHub Actions**  
✅ How to **download and view test reports from GitHub**

---

## 🛠 Tools & Technologies Used

| Tool / Technology | Purpose |
|--------------------|----------|
| **Postman** | Create and execute API test cases |
| **Newman** | Run Postman collections from the command line |
| **newman-reporter-htmlextra** | Generate detailed HTML reports |
| **GitHub Actions** | Automate test execution pipelines |
| **Node.js** | Required for running Newman |
| **Restful Booker API** | A public API used for demo and testing |

---

## 🗂 Project Structure
```
PostmanReports/
│
├── Restful Booker BVT.postman_collection.json     # Postman test cases
├── Production.postman_environment.json            # API environment configuration
│
├── .github/workflows/
│   ├── github-actions-demo.yml                    # Basic test workflow
│   └── github-actions-htmlextra-report.yml        # Workflow with HTML report
│
└── README.md                                     # Project documentation
``` 
---

## 🚀 Step-by-Step Setup Guide

### 🧰 Prerequisites

Before you begin, make sure the following tools are installed on your computer:

| Tool | Description | Download |
|:--:|:--|:--|
| <img src="https://raw.githubusercontent.com/github/explore/main/topics/nodejs/nodejs.png" width="30"/> | **Node.js** – Needed to install and run **Newman** (the Postman CLI). | [🔗 Node.js](https://nodejs.org/) |
| <img src="https://raw.githubusercontent.com/github/explore/main/topics/postman/postman.png" width="30"/> | **Postman** – Create and manage API test collections. | [🔗 Postman](https://www.postman.com/downloads/) |
| <img src="https://raw.githubusercontent.com/github/explore/main/topics/git/git.png" width="30"/> | **Git** – Clone this repo and use version control. | [🔗 Git](https://git-scm.com/) |
| <img src="https://raw.githubusercontent.com/github/explore/main/topics/github/github.png" width="30"/> | **GitHub** – To host your repo and run **GitHub Actions**. | [🔗 GitHub](https://github.com/) |

> 💡 These tools form the complete setup for running and automating API tests in this project.

---

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/upenanuhansi/PostmanReports.git
cd PostmanReports
```

2️⃣ Install Newman and HTML Extra Reporter
Install Newman and the HTML Extra reporter globally:

```bash
npm install -g newman
npm install -g newman-reporter-htmlextra
```

3️⃣ Run the Postman Tests Locally
```bash
newman run "Restful Booker BVT.postman_collection.json" \
-e "Production.postman_environment.json" \
-r htmlextra \
--reporter-htmlextra-export testResults/htmlreport.html
```
This command will:
  - Run all the Postman tests in your collection
  - Use the provided Production environment
  - Generate a professional-looking HTML report in a folder called ```testResults/```
    
---

## ⚙️ Automating Tests with GitHub Actions

The repository includes two GitHub Actions workflows inside ```.github/workflows/```.

🧱 ```github-actions-demo.yml```

A basic workflow that:
- Runs Newman tests using the Postman Docker container
- Executes all tests in your collection

🖼 ```github-actions-htmlextra-report.yml```

An advanced workflow that:
- Installs Node.js and Newman
- Runs the Postman tests
- Generates a detailed HTML Extra report
- Uploads the report as a downloadable artifact in GitHub Actions
Once you push code, GitHub will automatically run the workflow.

---

## 👀 Viewing Test Reports

After the workflow completes:

1. Go to your repository on **GitHub**
2. Click the **Actions** tab
3. Open the **latest workflow run**
4. Scroll down to the **Artifacts** section
5. Download the artifact named **RunReports**
6. Open the file **`htmlreport.html`** in your browser to view the report


### 📊 You’ll See:

- ✅ **Test summary** with pass/fail results  
- 🧾 **Detailed request and response logs**  
- 📈 **Charts and graphs** for response times  
- ❗ **Assertion and error details** for debugging  

> 💡 Tip: The HTML Extra Reporter generates an interactive report where you can expand each request to view the request body, response, test scripts, and console logs.

---
## 🧠 How the Collection Works

The Postman collection — ```Restful Booker BVT.postman_collection.json``` — tests the following API functionalities:
| Category              | Endpoint        | Description                               |
| --------------------- | --------------- | ----------------------------------------- |
| **Get Bookings**      | `/booking`      | Fetch all bookings or filter by name/date |
| **Get Booking by ID** | `/booking/{id}` | Retrieve details of a specific booking    |
| **Create Booking**    | `/booking`      | Create a new booking                      |
| **Modify Booking**    | `/booking/{id}` | Update existing booking (PUT)             |
| **Patch Booking**     | `/booking/{id}` | Partial update (PATCH)                    |
| **Delete Booking**    | `/booking/{id}` | Delete a booking                          |
| **Auth**              | `/auth`         | Generate token for secure access          |
| **Ping**              | `/ping`         | Check API health                          |

Each request:
    - Sends data to the API
    - Runs automated JavaScript-based tests (using ```pm.test()``` in Postman)
    - Validates the response, status code, and data integrity
    
---

## 🧾 Example of What You’ll See in Reports

  ✅  Total tests passed and failed   
  📊  Response time and performance charts  
  🧩  Detailed breakdown of each API call  
  🕵️‍♀️  Assertions, failures, and request payloads  
  💬  Logs showing dynamic variables and test steps
  
---

## 📘 Learning Notes

If you’re new to API testing or CI/CD, here’s the ideal order to learn:
  1. Understand APIs — Learn what endpoints, requests, and responses are.
  2. Postman Basics — Create and organize API requests in Postman.
  3. Test Scripts — Write JavaScript-based tests inside Postman.
  4. Export Collections — Save and share your Postman collections.
  5. Newman CLI — Run Postman tests automatically via command line.
  6. HTML Reporter — Visualize results in user-friendly reports.
  7. GitHub Actions — Automate the whole testing workflow.
  
---

## 🏆 Credits

  - Learning Source: AskHerConsulting
  - API: Restful Booker
  - Tools: Postman, Newman, newman-reporter-htmlextra, GitHub Actions
  - Author: Nuhansi

---

## 💡 Final Notes

This project is a great foundation for learning:
  - Continuous Integration (CI)
  - Automated API Testing
  - GitHub Workflow Automation

Once you understand this setup, you can adapt it to any API project — whether it’s your own app or a company project.
