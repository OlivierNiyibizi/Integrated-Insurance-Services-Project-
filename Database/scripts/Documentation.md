**my documentation for database**

**Integrated Insurance Services Project – Simple Documentation**
**1. Project Overview**

The Integrated Insurance Services Project is a database system designed to help an insurance company manage its daily activities. The system stores and organizes information about customers, insurance policies, payments, and claims. It also uses PL/SQL automation to make the system faster and more accurate.

**2. Purpose of the System**

The main purpose of this project is to:

Replace manual paperwork with a computerized database

Keep all insurance information in one place

Reduce errors and missing information

Automate repetitive tasks

Make it easier for administrators to manage insurance operations

**3. Main Features**
a. Customer Management

Stores customer details such as name, phone number, email, and registration date.

b. Policy Management

Stores information about different insurance policies offered by the company.

c. Customer Policy Assignment

Connects each customer to the policy they have purchased, including start and end dates.

d. Payment Tracking

Keeps records of all payments made by customers for their policies.

e. Claim Processing

Stores all claims submitted by customers and tracks their status (Pending, Approved, or Rejected).

**4. Tables in the Database**

**The system contains 5 main tables:**

1. CUSTOMER

Stores personal information of customers.

2. POLICY

Stores types of insurance policies and their details (premium, coverage, duration).

3. CUSTOMER_POLICY

Links a customer to the policy they bought.
It also shows if a policy is active or expired.

4. PAYMENT

Stores information about payments for each customer’s policy.

5. CLAIM

Stores information about claims customers make when they need compensation.

**5. Automation Using PL/SQL**

**The project includes automation to make work easier:**

a. Premium Calculation

A procedure that displays the premium amount for a selected customer policy.

b. Claim Approval

A procedure that automatically updates the claim status to "Approved" with an approved amount.

c. Policy Status Update

A trigger that automatically changes a policy status from "Active" to "Expired" when the end date has passed.

d. Payment Validation

A trigger that checks if a customer has paid before a policy becomes active.

**6. Benefits of the System**

Ensures accurate customer and policy records

Saves time for administrators

Reduces human mistakes

Makes claim processing faster

Tracks payments and policy status automatically

Provides better transparency and reporting

**7. Conclusion**

This project offers a complete insurance management system using a relational database and PL/SQL automation. It improves the speed, accuracy, and reliability of insurance operations. The system can be expanded in the future to include more services such as online customer access, reminders, and notifications.
