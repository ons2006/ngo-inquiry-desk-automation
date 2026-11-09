# ngo-inquiry-desk-automation

# Non-Profit Inquiry Desk Automation

A no-code workflow that helps a small non-profit handle incoming messages faster: it categorizes each inquiry, sets a priority, prepares a draft reply, and notifies the team automatically.

## Problem
Small non-profits receive questions, donation offers, volunteer requests, and complaints through one contact form. Sorting and answering them by hand is slow, and urgent messages can be missed.

## Solution
A Google Form sends each message to a Google Sheet. Formulas in the sheet categorize the message and set its priority. Two Zapier workflows then send emails automatically.

## Tools
Google Forms, Google Sheets , Zapier , Gmail

## How it works
1. A person submits the contact form (name, email, message).
2. The answer is added as a new row in Google Sheets.
3. A formula assigns a **Category**: Donation, Volunteering, Partnership, Complaint, or Question (keyword rules in English and French).
4. A second formula assigns a **Priority**: High, Medium, or Low.
5. A third formula writes a **template-based draft reply** for that category.
6. **Zap 1:** sends an automatic confirmation email to the sender.
7. **Zap 2:** sends the coordinator an email with the message, category, priority, and draft reply.

## Screenshots
Available in screenshots folder

## Demo video
Available in screenshots folder

## Example formula (category)
Google Sheets set to French uses semicolons and French function names:

    =ARRAYFORMULA(SI(D2:D="";"";SI(REGEXMATCH(MINUSCULE(D2:D);"donat|don|argent|fund|money");"Donation";"Question")))

(Shortened here. The full version has all five categories.)

## Results
- Tested on sample messages in English and French
- categorized correctly
- Handling time per message: about [10 minutes] by hand, [under 1 minute] with the workflow
- Important: all test data is fake

## Limitations
- Categories use **keyword rules**, so messages without these keywords fall into "Question"
- Draft replies are templates, not AI-generated, and a human should review them before sending
- The free Zapier plan allows only two-step Zaps, 100 tasks per month, and has a delay of several minutes between steps
