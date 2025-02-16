- AWS Organisations allow you to manage multiple accounts.
- There is always 1 management account which pays all the bills, and many member accounts.
- You can also make organisational units (OUs) which are subgroups within the root OU, and these can be as nested as you want.

**So why do this?**
- The accounts can all share reserved instances and saving plans across the accounts
- Having separate accounts provides a better separation of concerns than 1 account with many VPCs

**Security**
- Use **service control policies (SCP)** which are policies which themselves determine what the IAM policies within an account can do, they can be applied to an entire OU or an account.
- These policies **do not apply to management account**, which always has full admin power (otherwise you could lock yourself out)
- For an account to do something it must inherit an explicit allow from its parent OU (or above), also, a child OU/account cannot override greater permissions that it inherits - ie it cannot grant access to something denied above.


You can take a blocklist or allowlist strategy with SCPs - depending on how secure you want to be.
- Either allow everything and then deny specific resources
- Or just put allows on specific resources (with no allow, the default will be deny)