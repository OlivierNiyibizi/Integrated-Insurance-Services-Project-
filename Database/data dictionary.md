Business Process Modeling Integrated Insurance Services (MIS-based Insurance Workflow)

1. Scope Definition

Business Process Modeled:

Insurance Service Workflow

covering customer registration, policy assignment, payment validation,

policy activation, and claim processing.

MIS Relevance:

The process relies heavily on the Integrated Insurance MIS, built with

PL/SQL triggers, procedures, and centralized databases that automate:

• Customer registration

• Policy linking

• Payment validation

• Automatic policy activation/expiration

• Claims approval or rejection

Objectives

• Digitize all insurance operations

• Reduce errors from manual paperwork

• Enable automation through PL/SQL triggers

• Improve decision-making for policy activation and claims

• Deliver accurate, real-time information

Expected Outcomes

• Faster customer service

• Automatic policy management

• Transparent claim decision process

• Centralized and accurate data storage

• Improved organizational efficiency

2. Key Entities

Users / Actors

• Customer – requests registration, buys insurance, submits claims

• Agent – registers customers and assigns policies

• Finance Officer – processes and verifies payments

• Claims Officer – validates and processes claims

• MIS System – automates updates, validates consistency, manages data

Departments/Systems

• Customer Service

• Policy Management Unit

• Finance Department

• Claims Department

• MIS/Database System (PL/SQL powered)

Data Sources (Database Tables)

CUSTOMER – customer personal records

POLICY – insurance policy details

CUSTOMER_POLICY – purchased policies

PAYMENT – payment tracking

CLAIM – claim requests and status

Roles & Responsibilities

• Agent: Registers customer, assigns policies

• Finance Officer: Confirms payments, activates policies

• Claims Officer: Reviews claim requests, updates status

• MIS: Automatically updates statuses, validates data, triggers workflows

3. Swimlane Requirements (for your diagram)

Your diagram MUST include these swimlanes:

Customer

Agent

Finance Officer

Claims Officer

MIS System

Each activity stays in its lane to show responsibilities and handoff points.

4. BPMN/UML Notation Requirements

Use these elements in Lucidchart/Canva/draw.io:

• Start Event – green circle

• End Event – red circle

• Task – rounded rectangle

• Gateway/Decision – diamond

• Data Objects – document symbol

• Swimlanes – for departments

5. Logical Flow (Step-by-Step Process)

This is EXACTLY what your diagram should show:

A. Customer Registration

Start

Customer requests registration

Agent enters customer data into MIS

MIS saves data into CUSTOMER table

B. Policy Assignment

Customer selects policy

Agent assigns policy → MIS

MIS creates entry in CUSTOMER_POLICY

C. Payment + Policy Activation

Finance Officer receives payment

Finance updates MIS with payment info

MIS stores record in PAYMENT table

Decision: Payment valid?

• No → MIS marks policy as Pending, notify customer → End

• Yes → Trigger activates policy (PL/SQL)

MIS updates policy status to Active
D. Claims Request

Customer submits claim

Claims Officer enters details → MIS

MIS stores entry in CLAIM table

Decision: Claim approved?

• Rejected → MIS marks claim as Rejected → End

• Approved → MIS calculates approved amount automatically

MIS updates claim status to Approved

End

6. MIS Functions in This Process

• Data validation during registration and policy assignment

• Automatic policy expiration check (PL/SQL triggers)

• Payment verification workflow

• Automatic activation after payment

• Claim approval calculation logic

• Centralized reporting (Dashboards) for:

o Active vs expired policies

o Payment history

o Claim statistics

7. Organizational Impact

• Eliminates paperwork and scattered records

• Enhances transparency (full history visible)

• Speeds up claims approval and policy activation

• Improves accountability between departments

• Allows managers to make data-driven decisions

8. Analytics Opportunities

With MIS data, the company can analyze:

• Frequently purchased policy types

• Customer retention rate

• Most common claim types

• Revenue prediction (premiums)

• Fraud detection using claim patterns

• Peak periods for registration and payments
