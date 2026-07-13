# ⭐ Customer Feedback Analyzer

A beginner-friendly workflow built using **n8n** to automate customer feedback analysis. The workflow reads customer reviews from Google Sheets, separates positive and negative feedback based on ratings, organizes feedback into different rating categories, generates useful statistics, and sends an automated report to the customer support team.

This project helped me practice conditional workflows, data sorting, summarization, branching, and automation using n8n.

---

# 📌 Project Overview

The workflow automatically performs the following tasks:

- Reads customer feedback from Google Sheets
- Classifies feedback into Positive and Negative
- Stores positive and negative feedback separately
- Organizes feedback based on ratings (1–5)
- Finds the Top 10 Lowest Rated Products
- Counts feedback entries for each product
- Generates a summary report
- Sends an email to the customer support team

---

# 🚀 Workflow

```text
Schedule Trigger
        │
        ▼
Update Google Sheet
        │
        ▼
Read Customer Feedback
        │
        ▼
IF (Rating < 3)
 ┌───────────────┐
 │               │
 ▼               ▼
Negative      Positive
Feedback      Feedback
 │               │
 ▼               ▼
Sort         Save to Sheet
 │
 ▼
Negative Feedback Sheet
        │
        ▼
Merge
        │
 ┌──────┼──────────────────────────────┐
 │      │              │               │
 ▼      ▼              ▼               ▼
Switch  Sort         Summarize       Code
 │       │               │             │
 │       ▼               ▼             ▼
 │    Limit(10)    Product Count   Summary Report
 │       │               │             │
 ▼       ▼               ▼             ▼
Rating Sheets   Google Sheet   Gmail + Summary Sheet
```

---

# 🛠 Nodes Used

| Node | Purpose |
|------|---------|
| Schedule Trigger | Runs the workflow automatically |
| Google Sheets | Read, update and append data |
| IF | Separate positive and negative feedback |
| Sort | Sort negative feedback and lowest-rated products |
| Merge | Combine workflow branches |
| Switch | Categorize feedback by rating |
| Summarize | Count feedback entries for each product |
| Limit | Select the lowest-rated 10 products |
| Code | Generate overall feedback statistics |
| Gmail | Send daily summary email |

---

# 📊 Workflow Logic

## Step 1

The workflow reads customer feedback from Google Sheets.

Each record contains:

- Customer Name
- Product
- Rating
- Feedback
- City

---

## Step 2

The IF node separates feedback into two groups.

### Negative Feedback

```
Rating < 3
```

Negative feedback is:

- Sorted by rating
- Saved into a separate Google Sheet

---

### Positive Feedback

```
Rating ≥ 3
```

Positive feedback is stored in a separate Google Sheet.

---

## Step 3

After processing both branches, the Merge node combines the data for further analysis.

---

## Step 4

The Switch node separates feedback into five different sheets.

Categories:

- ⭐ 1 Star
- ⭐⭐ 2 Stars
- ⭐⭐⭐ 3 Stars
- ⭐⭐⭐⭐ 4 Stars
- ⭐⭐⭐⭐⭐ 5 Stars

Each rating has its own Google Sheet.

---

## Step 5

The workflow sorts all products based on their rating.

The Limit node selects the **Top 10 Lowest Rated Products**, which are stored in a separate Google Sheet.

---

## Step 6

The Summarize node counts the number of feedback entries for each product.

Example:

| Product | Feedback Count |
|---------|---------------:|
| Laptop | 5 |
| Mouse | 3 |
| Router | 4 |
| Printer | 2 |

This helps identify products that receive the most customer feedback.

---

## Step 7

A Code node calculates overall statistics, including:

- Total Feedback
- Positive Feedback Count
- Negative Feedback Count
- Average Rating
- Highest Rating
- Lowest Rating

The summary is saved to a Google Sheet and used in the email report.

---

# 📧 Automated Email Report

The customer support team receives a daily report containing:

- Total Feedback Received
- Positive Feedback
- Negative Feedback
- Average Rating
- Highest Rating
- Lowest Rating

This allows the support team to quickly understand customer satisfaction and identify areas that need attention.

---

# 📚 Techniques Used

This project helped me practice the following n8n concepts:

- Workflow Automation
- Conditional Logic using IF
- Multi-Branch Workflows
- Data Sorting
- Data Limiting
- Data Merging
- Rating-Based Classification
- Product-wise Feedback Analysis
- Summary Report Generation
- JavaScript Code Node
- Automated Email Notifications
- Google Sheets Integration
- Scheduled Automation

---

# 🎯 What I Learned

While building this workflow, I learned how to:

- Separate data using IF conditions
- Organize records using Switch
- Sort data before processing
- Limit results to create Top 10 reports
- Count grouped data using Summarize
- Use JavaScript to calculate custom statistics
- Send automated email reports
- Build workflows with multiple branches

---

# 💻 Technologies Used

- n8n
- Google Sheets
- Gmail
- JavaScript (Code Node)

---

# 📂 Project Structure

```
customer-feedback-analyzer/
│
├── README.md
├── workflow.json
├── images/
│   ├── workflow.png
│   └── execution.png
└── sample-data/
    └── customer-feedback.csv
```

---

# 🚀 Future Improvements

Features I would like to add in future versions:

- Slack notifications
- Dashboard for customer feedback
- Monthly trend analysis
- AI-generated feedback summary
- Automatic sentiment analysis
- Charts for rating distribution
- PDF report generation
- Product performance dashboard

---

# 📸 Workflow Preview

## workflow Design

![image alt](https://github.com/n8n-workflows-projects/customer-feedback-analysis/blob/1acc64590e423390ce3aef20075a7e12f9c127f4/Screenshot%202026-07-13%20101942.png)
![image alt](https://github.com/n8n-workflows-projects/customer-feedback-analysis/blob/1acc64590e423390ce3aef20075a7e12f9c127f4/Screenshot%202026-07-13%20103243.png)

## workflow Resource
![image alt](https://github.com/n8n-workflows-projects/customer-feedback-analysis/blob/6f3863d028b9756e27cc2a7b8c2195f6d81cdb77/Screenshot%202026-07-13%20104248.png)

## workflow output
![image alt](https://github.com/n8n-workflows-projects/customer-feedback-analysis/blob/1acc64590e423390ce3aef20075a7e12f9c127f4/Screenshot%202026-07-13%20101757.png)
![image alt](https://github.com/n8n-workflows-projects/customer-feedback-analysis/blob/1acc64590e423390ce3aef20075a7e12f9c127f4/Screenshot%202026-07-13%20102001.png)
![image alt](https://github.com/n8n-workflows-projects/customer-feedback-analysis/blob/1acc64590e423390ce3aef20075a7e12f9c127f4/Screenshot%202026-07-13%20102726.png)



---

# 🙌 About This Project

I built this project while learning n8n to improve my understanding of workflow automation. It helped me practice working with Google Sheets, conditional logic, sorting, merging data, summarizing information, using JavaScript for custom calculations, and sending automated email reports. This project gave me more confidence in designing workflows that solve practical business problems.
