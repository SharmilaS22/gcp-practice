

Users, Groups, Service Accounts (used by services and other non human entitities)

Role - set of permissions - does not have any info about which users/sa's are using it
Policy - binds Role with User(s)/members, can have multiple bindings

IAM ROLES - 3 types

1. Basic roles - Not recommended for prod
    - Viewer, editer, Owner(editor + managing roles/permissions and billing)
    - this was used before IAM was created
2. Predefined roles:
    - single role for single purpose
    - Storage admin, Storage Object admin, Storage Object viewer etc
3. Custom roles

Policy binds
- principal (members - users, service accounts, groupd, domains web)
- roles (with sets of permissions)
- conditions


Policy troubleshooter - (like can-i in k8s)

gcloud iam roles


stages of policies - alpha, beta, generally available(GA), disabled.
initially the role created is in alpha stage, once you are confident move to GA

---

Service Accounts
- for resources like VMs
-  id-compute@developer.gserviceaccount.com
- uses private/public keys - not password
- both an identity and resource(can be assumed)

1. Default service accounts - not recommended - has editor access - can create service account with least permissions
2. google managed SA - used by gcp to perform operations on user's behalf


SA - used keys for auth - for gcp resources - the gcp manages internally
- but if an on prem/other vm outside of gcloud wants to access some resource and need an SA
    - For long lived(need for long time)
        - create an SA on gcp, and create a private key for the SA
        - Apps to access gcp resources - uses gcloud client libraries - it uses ADC(Application Default Credentials) which looks for GOOGLE_APPLICATION_CREDENTIALS env for SA creds
        - so set the path of the private key (for SA) to the env var GOOGLE_APPLICATION_CREDENTIALS
    - For short lived (few hours)
        - use oauth token / openid token /jwt token(self signed) etc for the SA

### Access to resource in another project
If an instance in Project A wants to access a bucket in Project B
1. Assign and Get the SA of the instance
2. In project B, assign the SA (email id) with bucket access permissions(roles)
3. So the SA of the instance can access the Bucket



---
### ACLs for bucket
- customised access for objects in a bucket
- user gets access if allowed in either iam or cli (one of them is enough)

Access control for buckets
- Uniform access(recommended) - Can give same access to all buckets/
objects
- Fine grained access - for objects - use acl


Signed urls:
- dont need google acc
- get key from SA/User (to be assumed)
- use key to sign the url (limited time)
```
gsutil signurl -d 10m gs://bucketname/object-path..
```
below members can be used to bind role to all
- allUsers - both authenticated and unauthenticated 
- allAuthenticatedUsers


Static hosting
- with custom domain - give bucket name same name as domain
- allow _Storage Object Viewer_ access to _allUsers_

