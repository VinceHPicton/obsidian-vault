Business logic is the set of rules and decisions that define how your app behaves in the real world.

Some examples:
- A user can't log in after 5 failed attempts
- Free shipping if order is over $100
- Interest is compounded daily
- Users can only follow up to 500 people
- Exactly 5 columns are required per CSV line

It's basically the logic defined by the code, and will primarily be in the backend (since we can't trust the frontend to enforce important rules).

The only business logic in the frontend will be things that help user experience like validation, but the backend will always need to recheck that these rules have been followed.