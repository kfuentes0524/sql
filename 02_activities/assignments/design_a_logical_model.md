# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

https://lucid.app/lucidchart/9f65cdd3-7e3a-4700-9c15-5ea6d798deef/edit?viewport_loc=-1412%2C-498%2C1997%2C891%2C0_0&invitationId=inv_2909ce76-6c7c-45b7-be19-ba8da1f7bde6

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.

https://lucid.app/lucidchart/9f65cdd3-7e3a-4700-9c15-5ea6d798deef/edit?viewport_loc=-1412%2C-498%2C1997%2C891%2C0_0&invitationId=inv_2909ce76-6c7c-45b7-be19-ba8da1f7bde6

## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
CUSTOMER_ADDRESS (Overwriting) Tipo 1
In this architecture, each time a customer updates their address, the old address is overwritten with the new one
customer_id (FK)
address_line1
address_line2
city
state
zip_code
country

CUSTOMER_ADDRESS (Retaining Address Changes) Tipo 2
In this architecture, each time a customer updates their address, the old address is retained and a new row is inserted with the updated address
customer_address_ID (PK)
customer_id (FK)
address_line1
address_line2
city
state
zip_code
country
star_date
end_date 

Privacy Considerations:
- Overwriting (Type 1): Minimizes privacy risks since only the latest address is stored. It aligns with data minimization principles, which is beneficial from a privacy and compliance perspective.
- Retaining (Type 2): While useful for business needs, this approach carries privacy risks as it stores more personal information over time. Retaining historical addresses may conflict with privacy regulations if customers want their old data erased or if data retention is restricted.

```

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
The AdventureWorks database uses highly normalized structures, splitting data into smaller, highly focused tables. For example, it separates sales information across multiple tables such as sales_territory, sales_person or sales_tax-rate. This structure reduces redundancy but increases complexity when querying for consolidated data. Additionally, this architecture is distributed for department While my ERD group more information into fewer tables. For example, the sales table in my ERD include fields for order-id, sales_price or quantity, making it easier to query but introducing potential redundancy.

My ERD prioritizes simplicity and ease of use, especially in smaller systems like a bookstore model, where quick access to customer, book or sales data is important. AdventureWorks focuses on scalability and data integrity, which is beneficial for large enterprise systems but can introduce complexity for developers when retrieving joined data.


```

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `September 28, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-4-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
