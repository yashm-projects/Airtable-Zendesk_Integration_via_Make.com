# Airtable-Zendesk_Integration_via_Make.com
This project automates the creation of Zendesk tickets directly from Airtable using Make.com  (formerly Integromat).

<img width="914" height="392" alt="image" src="https://github.com/user-attachments/assets/6f1cc71b-c0e8-4f6d-8a7e-63301d503313" />



**🔧 Use Case**

<img width="930" height="234" alt="image" src="https://github.com/user-attachments/assets/48f12344-f747-4f6b-bb85-a7e271826994" />

<img width="895" height="238" alt="image" src="https://github.com/user-attachments/assets/99f6caba-35e6-43d6-82f4-d1b90f07d02d" />


Teams log issues or requests in Airtable.

Each row has a flag (Send to Zendesk) that decides whether a ticket should be created.

If no Zendesk ticket exists for that row, Make.com automatically creates one in Zendesk and stores the Ticket ID back in Airtable.

This prevents duplicates and ensures Airtable and Zendesk stay in sync.

**⚙️ Flow Overview**

Trigger → Airtable “Watch Records”

Watches for new or updated rows.

Uses Created Time or Last Modified Time as the cursor.

Filter → Only send if:

Send to Zendesk = true

Zendesk Ticket ID is empty

Condition:
(Send to Zendesk = true) AND (Zendesk Ticket ID is empty)


Action → Zendesk “Create Ticket”

Maps Airtable fields → Zendesk fields (e.g., Subject, Description, Requester Email).

Update Airtable

After Zendesk ticket is created, writes the returned Ticket ID back into the Airtable row.

**📊 Example Airtable Setup**

<img width="471" height="222" alt="image" src="https://github.com/user-attachments/assets/d14f6960-8c97-4dca-82aa-5139be080aa4" />


**🚦 Error Handling**

If a ticket already exists (ID present), the filter skips the record.

Make.com automatically retries temporary API failures.

**✅ Benefits**

No manual copy-pasting between Airtable and Zendesk.

Avoids duplicate tickets.

Keeps both systems synchronized.

📌 Next Steps

Add bi-directional sync (update Airtable when ticket status changes).

Add notifications (e.g., Slack/Email when new ticket is created).
