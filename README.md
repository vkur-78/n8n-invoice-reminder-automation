# Invoice Reminder Automation using n8n

A production-ready invoice reminder automation built with **n8n**, **Google Sheets**, and the **WhatsApp Business API**.

The system automatically monitors invoices, due dates, customer credit limits, and post-dated cheques (PDC), sending timely WhatsApp notifications to customers, salespersons, and the accounts team.

---

## Features

### Workflow 1 – Invoice Reminder Automation

- 3 Days Before Due Date Reminder
- 1 Day After Due Date Reminder
- Monday Outstanding Summary (Customer-wise Aggregated)
- Salesperson Outstanding Summary (Tuesday & Friday)
- Automatic Reminder Logging
- Hold Customer Handling

### Workflow 2 – Credit & PDC Automation

- Credit Limit Exceeded Notification
- Customer PDC Reminder
- Accounts Team PDC Reminder
- Automatic PDC Processing

---

## Technology Stack

- n8n
- Google Sheets
- JavaScript
- WA Simple WhatsApp API
- WhatsApp Business Templates

---

## Repository Structure

```
README.md

ARCHITECTURE.md

WORKFLOW.md

workflows/
    invoice-reminder-workflow.json
    credit-limit-pdc-workflow.json
```

---

## Google Sheet

The workflow uses Google Sheets as the master data source.

Main columns include:

- Invoice Date
- Invoice Number
- Customer Name
- Customer Contact Number
- Balance Outstanding
- Salesperson Name
- Salesperson Contact Number
- Due Date
- Payment Status
- Hold Till Date
- PDC Date
- Credit Limit
- Credit Days

---

## WhatsApp Templates

Customer

- 3days_before_template_v1
- 1days_after_due_date
- monday_reminder
- pdc_customer_reminder

Salesperson

- salesperson_summary_v3
- credit_limit_exceeded_v2

Accounts

- pdc_accounts_reminder_v2

---

## Business Rules

- Ignore paid invoices.
- Skip reminders while customer status is Hold.
- Resume reminders after Hold Till Date.
- Aggregate Monday reminders customer-wise.
- Aggregate salesperson reminders salesperson-wise.
- Notify salesperson when credit limit is exceeded.
- Send PDC reminders one day before cheque date.
- Log successful reminders.

---

## Future Enhancements

- ERP Integration
- PostgreSQL
- Dashboard
- Collection Analytics
- Email Notifications
- AI Collection Assistant
- Multi-company Support

- 
<img width="1542" height="716" alt="Screenshot 2026-07-11 182903" src="https://github.com/user-attachments/assets/3f9062f7-95bf-457a-92dc-a4eca2f4e60e" />


<img width="1562" height="545" alt="Screenshot 2026-07-11 182929" src="https://github.com/user-attachments/assets/2417e85c-c8be-405c-a840-f7ca96f5f17f" />

- 

