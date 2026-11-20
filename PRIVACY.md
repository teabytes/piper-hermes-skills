# Piper privacy notice

Updated November 19, 2026.

Piper is a CSCI 599 coursework assistant operated by Aarti Lad for a dedicated class-only Google account containing fictional test data. It is not offered as a general public email service.

## Google account access

With the account owner's consent, Piper reads Gmail message headers, labels and snippets, counts drafts, and reads events on calendars owned by the account. It uses these results for inbox highlights, open-window calculations, meeting reminders and daily Telegram updates. It can create email drafts and send an allowlisted draft only after the configured owner reviews and approves it in Telegram. Google sign-in also supplies the account email to verify that the dedicated test account was selected.

## Processing and storage

The assistant runs on Google Cloud Run. Credentials are stored in Google Secret Manager; conversation, memory, task and scheduler state are saved in private Cloud Storage snapshots. Operational records are stored in Cloud Logging. Gmail and Calendar results used in tool-assisted conversations may be processed by the configured OpenAI cloud model, and summaries and reminders are delivered through Telegram. Local Gemma inference runs on the operator's Mac through a private Tailscale connection. Piper does not sell Google account data or use it for advertising.

## Control and contact

The account owner can revoke Piper's Google access at https://myaccount.google.com/connections. Revocation prevents future API access but does not automatically erase previously stored state, Telegram messages or exported coursework evidence. To request deletion of stored assistant data or ask about this notice, contact aarti.lad@gmail.com. Coursework evidence already submitted to the course is handled by the course's submission process.
