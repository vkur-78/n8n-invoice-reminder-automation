# System Architecture

```
                    Daily Scheduler
                          │
                          ▼
                  Google Sheets
                          │
                Read Invoice Records
                          │
                JavaScript Processing
                          │
        ┌─────────────────┴─────────────────┐
        │                                   │
        ▼                                   ▼
 Invoice Reminder Workflow         Credit & PDC Workflow
        │                                   │
        ▼                                   ▼
 WhatsApp Templates                WhatsApp Templates
        │                                   │
        └───────────────┬───────────────────┘
                        ▼
                  WA Simple API
                        │
      ┌─────────────────┼──────────────────┐
      ▼                 ▼                  ▼
  Customers        Salespersons       Accounts
```

---

# Components

## Scheduler

Runs daily according to configured Cron schedules.

---

## Google Sheets

Acts as the master database for

- Invoice Details
- Customer Details
- Salesperson Details
- Payment Status
- Hold Status
- Credit Limits
- PDC Dates

---

## Processing Layer

Responsible for

- Due Date Calculation
- Overdue Calculation
- Customer Aggregation
- Salesperson Aggregation
- Credit Limit Validation
- Hold Logic
- PDC Logic

---

## WhatsApp Layer

Creates template variables and sends approved WhatsApp template messages through WA Simple.

---

## Logging

Successful reminders update Google Sheets to prevent duplicate notifications and maintain reminder history.
