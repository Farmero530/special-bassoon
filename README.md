# special-bassoon
To perform tasks throughout multiple apps 
- Ask for Text -> RecipientRaw
- If RecipientRaw startswith "@"
    Set VenmoHandle = RecipientRaw
  Else
    Get Dictionary Value (Payees) for RecipientRaw -> VenmoHandle
    If VenmoHandle is empty
        Ask for Text -> VenmoHandle
- Ask for Number -> Amount
- Ask for Text -> Note
- Confirm via Alert ("Proceed"/"Cancel")
- Text -> VenmoURL (venmo://paycharge?txn=pay&recipients=@...&amount=...&note=...)
- URL Encode VenmoURL
- Open URL (Encoded VenmoURL)
- Wait (15s)
- Choose from Menu ("Cash Out in Cash App", "Skip Cash App")
- If Cash Out
    - Try Open URL (cashapp://cashout?amount=Amount)
    - Otherwise Open URL (cashapp://)
- Optional Telegram message via HTTP POST
- Speak: "Workflow finished"
