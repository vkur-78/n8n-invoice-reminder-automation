# Workflow Documentation

The project consists of two independent production workflows.

---

# Workflow 1

## Invoice Reminder Automation

This workflow manages all customer payment reminders and salesperson collection summaries.

### Reminder Types

### 1. Three Days Before Due Date

Trigger

↓

Read Invoice Sheet

↓

Pending Invoice

↓

Due in 3 Days

↓

Send Customer Reminder

↓

Update Reminder Status

---

### 2. One Day After Due Date

Trigger

↓

Pending Invoice

↓

Overdue by 1 Day

↓

Send Reminder

↓

Update Sheet

---

### 3. Monday Outstanding Reminder

Runs every Monday.

Process

Read invoices

↓

Filter overdue invoices

↓

Group by Customer

↓

Calculate Total Outstanding

↓

Generate Invoice Summary

↓

Send Single WhatsApp Message

↓

Update Sheet

---

### 4. Salesperson Summary

Runs every Tuesday and Friday.

Process

Read overdue invoices

↓

Group by Salesperson

↓

Group Customer Invoices

↓

Calculate Total Outstanding

↓

Generate Summary

↓

Send WhatsApp

---

### Hold Logic

If

Payment Status = Hold

AND

Hold Till Date ≥ Today

↓

Skip Reminder

Else

Continue Processing

---

# Workflow 2

## Credit Limit & PDC Automation

This workflow handles credit control and post-dated cheque reminders.

---

### Credit Limit Monitoring

Read Invoice Sheet

↓

Calculate Customer Outstanding

↓

Outstanding > Credit Limit

↓

Notify Salesperson

↓

End

---

### Customer PDC Reminder

Read PDC Date

↓

Cheque Date = Tomorrow

↓

Send Customer Reminder

↓

End

---

### Accounts PDC Reminder

Read PDC Date

↓

Cheque Date = Tomorrow

↓

Notify Accounts Team

↓

Fill Cheque Deposit Form

↓

Deposit Cheque

---

# Workflow Schedule

| Workflow | Frequency |
|-----------|-----------|
| 3 Days Before Reminder | Daily |
| 1 Day After Reminder | Daily |
| Monday Customer Summary | Every Monday |
| Salesperson Summary | Tuesday & Friday |
| Credit Limit Check | Daily |
| Customer PDC Reminder | Daily |
| Accounts PDC Reminder | Daily |

---

# Message Recipients

## Customer

- 3 Days Before Reminder
- 1 Day After Reminder
- Monday Outstanding Summary
- PDC Reminder

## Salesperson

- Outstanding Summary
- Credit Limit Exceeded Notification

## Accounts

- PDC Deposit Reminder

---

# Production Notes

- Uses approved WhatsApp templates.
- Supports customer-wise aggregated reminders.
- Supports salesperson-wise aggregated summaries.
- Prevents duplicate reminders using update flags.
- Designed for easy migration from Google Sheets to an ERP or database.
