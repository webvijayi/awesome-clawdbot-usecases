# Invoice Chaser

> Automated invoice tracking and payment reminders for freelancers and small businesses

## The Problem

Chasing unpaid invoices is awkward, time-consuming, and easy to forget—leading to cash flow problems that kill otherwise healthy businesses. Freelancers especially struggle: you're busy doing actual work, and manually tracking who owes what, when it's due, and who needs a nudge feels like a second job. Meanwhile, that $3,000 invoice from 45 days ago quietly slips through the cracks.

## The Solution

OpenClaw becomes your accounts receivable assistant. It tracks invoices from email confirmations, manual input, or CSV imports, then automatically sends polite reminder emails at customizable intervals (7, 14, 30 days overdue). It learns which clients pay slow vs. fast, warns you about potential cash flow gaps, and keeps a running ledger you can query anytime with natural language ("Who owes me money?" / "What's my expected income this month?").

---

## Setup Guide

### Step 1: Create Your Invoice Tracker File

Create `invoices.json` in your OpenClaw workspace:

```bash
mkdir -p ~/openclaw/data
cat > ~/openclaw/data/invoices.json << 'EOF'
{
  "invoices": [],
  "clients": {},
  "settings": {
    "reminder_days": [7, 14, 30],
    "currency": "USD",
    "your_name": "YOUR NAME",
    "your_email": "your@email.com",
    "payment_terms": "Net 30"
  }
}
EOF
```

### Step 2: Create the Invoice Template

Create `~/openclaw/templates/invoice-reminder.md`:

```markdown
Subject: Friendly Reminder: Invoice #{{invoice_id}} - {{days_overdue}} days overdue

Hi {{client_name}},

I hope you're doing well! I wanted to follow up on Invoice #{{invoice_id}} for {{amount}} {{currency}}, which was due on {{due_date}}.

**Invoice Details:**
- Invoice #: {{invoice_id}}
- Amount: {{amount}} {{currency}}
- Due Date: {{due_date}}
- Days Overdue: {{days_overdue}}
- Description: {{description}}

If payment has already been sent, please disregard this message—and thank you!

If you have any questions or need to discuss payment arrangements, I'm happy to chat.

Best regards,
{{your_name}}
```

### Step 3: Set Up Email Access

Ensure OpenClaw has email skills configured. Add to your `skills/` directory or verify existing email integration works:

```bash
# Test email access
openclaw run "Check my inbox for any emails containing 'invoice' or 'payment'"
```

### Step 4: Add Your First Invoice

Simply tell OpenClaw:

```
Add invoice: Client "Acme Corp", $2,500 for "Website Redesign", 
invoice #INV-2024-001, due date Jan 15 2025, 
contact email: billing@acmecorp.com
```

### Step 5: Configure Cron Jobs (see section below)

### Step 6: Test the System

```
Show me all outstanding invoices
```

---

## Skills Needed

| Skill | Purpose | Required? |
|-------|---------|-----------|
| **Email (Gmail/IMAP)** | Send reminder emails, scan for payment confirmations | ✅ Yes |
| **File System** | Store invoice data in JSON | ✅ Built-in |
| **Calendar** | Track due dates, schedule follow-ups | ⚡ Recommended |
| **Web Search** | Verify client contact info if needed | ⚡ Optional |

### Minimal Setup (No Extra Skills)

Even without email skills, you can use OpenClaw to:
- Track invoices manually
- Get reminded via Telegram/Discord when invoices are overdue
- Generate reminder text you copy-paste into your email client

---

## Example Prompts

### Adding Invoices

```
Add invoice: "TechStart Inc" owes me $4,200 for "Q1 Consulting" 
(invoice #TS-2024-003), due Feb 1st 2025. 
Contact: accounts@techstart.io
```

```
I just sent invoice #2024-015 to Sarah at hello@sarahdesigns.co 
for $850 (logo design). Net 15 terms.
```

```
Bulk add these invoices from my spreadsheet:
- Client A, $1200, due Jan 20, inv #101
- Client B, $3400, due Jan 25, inv #102  
- Client C, $750, due Feb 1, inv #103
```

### Checking Status

```
What invoices are overdue right now?
```

```
Show me my accounts receivable aging report - 
who's 30+ days late?
```

```
How much money am I expecting this month? 
Break it down by client.
```

### Payment Tracking

```
Mark invoice #INV-2024-001 as paid - 
received $2,500 from Acme Corp today
```

```
Check my email for any payment confirmations 
in the last 48 hours and update my invoice tracker
```

### Client Insights

```
Which clients consistently pay late? 
Show me their average days-to-pay.
```

```
Based on my invoice history, forecast my cash flow 
for the next 60 days
```

### Sending Reminders

```
Draft a polite reminder email for all invoices 
that are 7+ days overdue - show me before sending
```

```
Send the standard 14-day reminder to TechStart Inc 
for invoice #TS-2024-003
```

---

## Cron Schedule

Add these to your OpenClaw cron configuration:

### Daily Invoice Check (9 AM)

```cron
0 9 * * * Check invoices.json for any invoices due today or overdue. For newly overdue invoices (just hit 7, 14, or 30 days), draft reminder emails and send them. Update the invoice record with reminder_sent timestamps. Notify me via Telegram of any actions taken.
```

**What it does:** Runs every morning at 9 AM. Catches invoices hitting reminder thresholds and sends appropriate emails automatically.

### Weekly Aging Report (Monday 8 AM)

```cron
0 8 * * 1 Generate a weekly accounts receivable report: total outstanding, breakdown by age (current, 1-7 days, 8-14 days, 15-30 days, 30+ days), and list any invoices needing escalation. Send summary to me via Telegram.
```

**What it does:** Every Monday morning, get a full picture of your outstanding invoices before the work week starts.

### Payment Confirmation Scanner (Every 6 hours)

```cron
0 */6 * * * Scan my email inbox for payment confirmations, bank notifications, or "paid" replies from clients. Cross-reference with invoices.json and mark matching invoices as paid. Log any payments found to memory/payments-YYYY-MM-DD.md
```

**What it does:** Automatically detects when clients pay and updates your records without manual intervention.

### Monthly Cash Flow Forecast (1st of month, 7 AM)

```cron
0 7 1 * * Analyze all outstanding invoices and historical payment patterns. Generate a 60-day cash flow forecast showing expected income by week. Factor in each client's average days-to-pay. Save report to data/cashflow-forecast-YYYY-MM.md and send summary via Telegram.
```

**What it does:** Start each month with visibility into expected income, adjusted for how quickly each client typically pays.

---

## HEARTBEAT.md Config

Add this section to your `HEARTBEAT.md`:

```markdown
## Invoice Chaser Checks

### Quick Invoice Scan (every heartbeat)
- [ ] Check if any invoices crossed a reminder threshold (7/14/30 days) since last check
- [ ] If yes: draft and send appropriate reminder email
- [ ] Update `data/invoices.json` with `last_reminder_sent` timestamp

### Payment Detection (2-3x daily)
- [ ] Scan recent emails for: "payment sent", "paid", "remittance", bank notifications
- [ ] Match against open invoices by amount, client name, or invoice number
- [ ] Mark matched invoices as paid in `data/invoices.json`
- [ ] Log to `memory/YYYY-MM-DD.md`: "💰 Payment received: $X from Client for Invoice #Y"

### State File
Track last check times in `memory/heartbeat-state.json`:
```json
{
  "invoiceChaser": {
    "lastReminderCheck": 1704067200,
    "lastPaymentScan": 1704038400
  }
}
```

### Alert Thresholds
- **Notify immediately** if: Invoice goes 45+ days overdue (escalation needed)
- **Notify immediately** if: Total overdue exceeds $5,000
- **Weekly summary** if: Any invoice aging report changes significantly
```

---

## Expected Results

### Week 1
- ✅ All existing invoices tracked in one place
- ✅ First automated reminders sent for overdue invoices
- ✅ You know exactly who owes you money

### Month 1
- ✅ 20-40% faster payment collection (industry average for automated reminders)
- ✅ Zero forgotten invoices
- ✅ Client payment pattern data starts building
- ✅ 2-3 hours/month saved on manual follow-ups

### Month 3+
- ✅ Accurate cash flow forecasting based on real client behavior
- ✅ "Slow payer" clients identified—adjust terms proactively
- ✅ Historical data for tax prep and business planning
- ✅ Professional, consistent follow-up without the awkwardness

---

## Sample Data Structure

Here's what your `invoices.json` looks like after a few months:

```json
{
  "invoices": [
    {
      "id": "INV-2024-001",
      "client": "Acme Corp",
      "client_email": "billing@acmecorp.com",
      "amount": 2500,
      "currency": "USD",
      "description": "Website Redesign",
      "issued_date": "2024-12-15",
      "due_date": "2025-01-15",
      "status": "paid",
      "paid_date": "2025-01-18",
      "days_to_pay": 34,
      "reminders_sent": ["2025-01-22"]
    },
    {
      "id": "INV-2024-002",
      "client": "TechStart Inc",
      "client_email": "accounts@techstart.io",
      "amount": 4200,
      "currency": "USD",
      "description": "Q1 Consulting",
      "issued_date": "2025-01-02",
      "due_date": "2025-02-01",
      "status": "outstanding",
      "reminders_sent": []
    }
  ],
  "clients": {
    "Acme Corp": {
      "avg_days_to_pay": 34,
      "total_invoiced": 7500,
      "total_paid": 5000,
      "payment_reliability": "slow"
    },
    "TechStart Inc": {
      "avg_days_to_pay": 12,
      "total_invoiced": 12600,
      "total_paid": 8400,
      "payment_reliability": "fast"
    }
  },
  "settings": {
    "reminder_days": [7, 14, 30],
    "currency": "USD",
    "your_name": "Jane Freelancer",
    "your_email": "jane@janefreelance.com",
    "payment_terms": "Net 30"
  }
}
```

---

## Pro Tips

1. **Start simple**: Just track invoices manually for week 1. Add automation once you trust the data.

2. **Customize reminder tone**: Edit the template for each interval—day 7 is friendly, day 30 is firmer.

3. **Integration opportunity**: If you use FreshBooks/QuickBooks/Xero, ask OpenClaw to parse their notification emails automatically.

4. **The nuclear option**: For 60+ day invoices, have OpenClaw draft a "final notice before collections" email for your review.

5. **Celebrate payments**: Configure OpenClaw to send you a 🎉 reaction when a payment is detected. Small wins matter.

---

*Setup time: ~20 minutes | Maintenance: ~5 min/week | ROI: Priceless sanity*
