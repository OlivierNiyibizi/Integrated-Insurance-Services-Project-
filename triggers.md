Example Trigger: Auto Expire Policies

<img width="498" height="223" alt="image" src="https://github.com/user-attachments/assets/9cbac328-393c-41c8-a1ec-eda627d70a21" />


How it works
•	Fires before any INSERT or UPDATE on CUSTOMER_POLICY.
•	Checks if the end_date is already past.
•	If so, it automatically sets the status column to 'Expired'.
•	This ensures consistency without relying on manual updates.
Another Practical Trigger: Audit Payments
<img width="491" height="202" alt="image" src="https://github.com/user-attachments/assets/edc10161-59dd-4059-a9ec-278f16ff6c71" />


How it works
•	Fires after a new payment is inserted.
•	Logs the event into an AUDIT_LOG table (you’d need to create it).
•	Captures timestamp, user, action, and details.

<img width="249" height="36" alt="image" src="https://github.com/user-attachments/assets/9dcc08d4-b5a4-400d-9431-f03cc14eaa4b" />
<img width="252" height="31" alt="image" src="https://github.com/user-attachments/assets/9573ed6b-de8f-43a4-bd3e-966edee3829b" />

<img width="1010" height="173" alt="image" src="https://github.com/user-attachments/assets/7e41186b-671d-40fb-a76f-c379db1e590f" />



