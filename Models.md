This page contains a breakdown of the models within the system.

## ERD
![Entity Relationship Diagram for the NewERA platform](https://drive.google.com/file/d/1MoR7NglzlB7UrP2poZhehi4HtH9fYRDk)
https://drive.google.com/file/d/1MoR7NglzlB7UrP2poZhehi4HtH9fYRDk/view?usp=sharing

## Models

### User
Defines a user that has an account associated with the system; they are either an admin or an SOW. Extends Django's AbstractUser class, so the user can log in and out of the system and has the ability to change or reset their passwords. *is_superuser* corresponds with *admin*, and *is_staff* corresponds with an *SOW*.

### CaseLoadUser
Defines an individual on a user's case load. CaseLoadUsers cannot log into the system. A CaseLoadUser can only belong to one User.

### Referral
Represents a transaction of resources made by a single User. Referrals must have a User, but they do not need a CaseLoadUser. A referral without a CaseLoadUser represents a referral to someone out of the app system, while a referral with a CaseLoadUser represents a referral to a User's CaseLoadUser. A referral can include many resources.

### Resource
Represents the basic item used in referrals and which can be accessed freely on the site. Resources are referred to individuals, but they can exist without being referred. A resource can also have many tags, though it does not need any.

### Tag
Represents a category that a resource fits into. Used specifically in filtering resources. Resources can have multiple tags, and tags can have multiple resources, but a resource does not need to be tagged, and a tag does not need to be associated with any resources.
