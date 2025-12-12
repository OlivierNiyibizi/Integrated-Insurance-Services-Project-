**inserting data into tables**

**customer table**
INSERT INTO CUSTOMER (Full_Name, Phone, Email) VALUES ('Alice Johnson', '0788123456', 'alice@example.com');

INSERT INTO CUSTOMER (Full_Name, Phone, Email) VALUES ('Bob Smith', '0788234567', 'bob@example.com');

<img width="515" height="121" alt="image" src="https://github.com/user-attachments/assets/f99ae476-b1ff-4972-9b35-0b5391b3bffc" />

**policy table**

INSERT INTO POLICY (Policy_name, Policy_type, Premium_amount, Coverage_amount, Duration_months)
VALUES ('Travel Secure', 'Travel', 120.00, 5000.00, 6);

<img width="610" height="102" alt="image" src="https://github.com/user-attachments/assets/a41e15a0-f66e-4916-b9ca-0d0c8037fa05" />

**customer_policy table**

INSERT INTO CUSTOMER_POLICY (Customer_id, Policy_id, Start_date, End_date, Status)
VALUES (1, 1, SYSDATE, ADD_MONTHS(SYSDATE, 12), 'Active');

INSERT INTO CUSTOMER_POLICY (Customer_id, Policy_id, Start_date, End_date, Status)
VALUES (2, 2, SYSDATE, ADD_MONTHS(SYSDATE, 12), 'Active');

<img width="524" height="63" alt="image" src="https://github.com/user-attachments/assets/64dd9f16-5b8a-4944-928e-4cd5762ed4ce" />

**payment table**

INSERT INTO PAYMENT (Customer_policy_id, Amount_paid, Payment_method)
VALUES (1, 200.00, 'Credit Card');

INSERT INTO PAYMENT (Customer_policy_id, Amount_paid, Payment_method)
VALUES (2, 150.00, 'Cash');

<img width="515" height="72" alt="image" src="https://github.com/user-attachments/assets/ba766f2f-1092-4a4e-bf06-cc95d4f44084" />

**claim table**

INSERT INTO CLAIM (Customer_policy_id, Claim_description)
VALUES (1, 'Hospitalization due to accident');

INSERT INTO CLAIM (Customer_policy_id, Claim_description)
VALUES (2, 'Car accident damage');

<img width="720" height="64" alt="image" src="https://github.com/user-attachments/assets/73b8bdc9-1cd6-4675-9738-d24f11217c13" />


