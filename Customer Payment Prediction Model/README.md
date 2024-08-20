# Project: Customer Payment Prediction Model

## Overview
This project involves a vendor who manages multiple customer companies. The dataset includes the following columns:

- **Customer Number**: Unique identifier for each customer.
- **Customer Name**: Name of the customer company.
- **Transaction ID**: Identifier for each transaction.
- **Transaction Due Date**: The deadline for the customer to submit their payment.
- **Deposit Date**: The date when the customer actually deposited their payment.
- **Application Amount**: The amount involved in the transaction.
- **Currency**: The currency in which the transaction was made.

## Project Objective
The objective is to develop a model that, when generating an invoice for a customer on the current date, will analyze past payment records to predict whether the customer typically makes payments on time or with delays.


## Pivot Table Summary

This pivot table provides the following insights for each customer:

- **Average Days Past Due**: The average number of days a payment is overdue. Negative values indicate early payments.
- **Standard Deviation of Days Past Due**: The variability in the number of days past due.
- **Total Number of Late Payments**: The total count of late payments made by the customer.
- **Average of On-Time Payments**: A value of 1 indicates the customer always pays on time, while 0 indicates they never pay on time.

### Key Observations:

- **Amdocs and Flipkart**: Both have an average of 1.0 for on-time payments, indicating they consistently pay on time or early.
- **Organization 80**: Has the highest number of late payments (1002) among the customers displayed.
- **Organization 458**: Exhibits a very high average of days past due (379 days).
- **Organization 80**: Despite having a high number of late payments (1002), this organization still pays on time about half the time.
