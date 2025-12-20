Example Trigger: Auto Expire Policies
sql
CREATE OR REPLACE TRIGGER trg_expire_policy
BEFORE UPDATE OR INSERT ON customer_policy
FOR EACH ROW
BEGIN
  -- If the end_date is before today, mark status as Expired
  IF :NEW.end_date < SYSDATE THEN
    :NEW.status := 'Expired';
  END IF;
END;
/
How it works
•	Fires before any INSERT or UPDATE on CUSTOMER_POLICY.
•	Checks if the end_date is already past.
•	If so, it automatically sets the status column to 'Expired'.
•	This ensures consistency without relying on manual updates.
Another Practical Trigger: Audit Payments
sql
CREATE OR REPLACE TRIGGER trg_audit_payment
AFTER INSERT ON payment
FOR EACH ROW
BEGIN
  INSERT INTO audit_log (event_ts, user_name, action, details)
  VALUES (SYSDATE, USER, 'PAYMENT_INSERT',
          'Payment of ' || :NEW.amount_paid || ' by method ' || :NEW.payment_method);
END;
/
How it works
•	Fires after a new payment is inserted.
•	Logs the event into an AUDIT_LOG table (you’d need to create it).
•	Captures timestamp, user, action, and details.

<img width="249" height="36" alt="image" src="https://github.com/user-attachments/assets/9dcc08d4-b5a4-400d-9431-f03cc14eaa4b" />
<img width="252" height="31" alt="image" src="https://github.com/user-attachments/assets/9573ed6b-de8f-43a4-bd3e-966edee3829b" />

<img width="1010" height="173" alt="image" src="https://github.com/user-attachments/assets/7e41186b-671d-40fb-a76f-c379db1e590f" />



