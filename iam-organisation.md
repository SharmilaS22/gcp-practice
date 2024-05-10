one project per environment per applicaation

Billing Account -> contains Payment details

Organisation -> Folder/Billing-Account -> Project -> Resources

Organisation -> Folders and Billing Accounts

Projects should be associated with Billing Accounts for creating resources

Billing Accounts -> one or more Projects

Separate billing account for each department in large enterprise

Two types:
- Self serve - billed directly to Credit card/bank acc
- Invoiced - generate invoice and pay 


Cloud Billing Budget - add alerts with threshold and 50%, 90% etc - alert by email
- can send alerts to pub/sub

Two exports - BigQuery Export / File Export
- Can export to big query
- Can export to GCS for archival

Best practices
- Least privilege
- use service account for each apps if each need different privileges
- Separation of privileges - one does not have all
- constant monitoring of audit changes in IAM
- using groups 


Federation of other identities to use gcp
Identity platform