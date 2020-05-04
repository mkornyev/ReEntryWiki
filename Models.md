This page contains a breakdown of the models within the system.

## ERD
https://drive.google.com/file/d/1MoR7NglzlB7UrP2poZhehi4HtH9fYRDk/view?usp=sharing

## Models

### `User`
Defines a user that has an account associated with the system; they are either an admin or an SOW. Extends Django's AbstractUser class, so the user can log in and out of the system and has the ability to change or reset their passwords. 
* __*is_superuser* corresponds with *admin*, and *is_staff* corresponds with an *SOW*.__

### `CaseLoadUser`
Defines an individual on a user's case load. CaseLoadUsers cannot log into the system. __A CaseLoadUser can only belong to one User.__
* Admins see all `CaseLoadUser`s
* SOWs see only those belonging to them

### `Referral`
Represents a transaction of resources made by a single User. Referrals must have a User, but they do not need a CaseLoadUser. A referral without a CaseLoadUser represents an out-of-system referral, while a referral with a CaseLoadUser represents a referral to a User's CaseLoadUser. A referral can include many resources.
* __Notifications:__ 
  1. Types: The referral model contains `sendSMS` and `sendEmail` methods that fire when a referral is created 
  2. Referral Tracking: The system uses a verification mechanism to check whether a referral link (for a particular resource) was accessed by the user. It does this by generating a `created_at` object for the referral, and appending it as a querystring to each link. If the param is seen again by the server (in the __get_resource__ or __home__ actions), the `markReferralAsSeen()` function matches the timestamp to a referral marks it as seen. `THIS IS A CRUCIAL APPLICATION MECHANISM` 
    * Although collisions are possible, they are highly unlikely. The `Str()` representation of the object contains SIX decimal points. [Read more here](https://docs.python.org/2/library/datetime.html#datetime.datetime.__str__)

### `Resource`
Represents the basic item used in referrals and which can be accessed freely on the site. Resources are referred to individuals, but they can exist without being referred. A resource can also have many tags, though it does not need any.
* Resource Images (type: [`django.db.models.fields.FileField`](https://docs.djangoproject.com/en/3.0/ref/models/fields/#filefield)):
  * These are stored in the application's `MEDIA_ROOT` directory (currently `NewERA/user_uploads`)
  * They are validated by the ResourceForm, and have an upload limit.
  * A `content_type` field is used to store image types: This is required because prior to validation, images are stored as an in memory type (native) and then converted to a FileField type, thereby losing their .content_type attributes. See the try/except block in __views.py__ `edit_resource` function. 
  * The default Django forms mechanism is not used to implement uploads. Instead, images they are removed from the filesystem manually 

### `Tag`
Represents a category that a resource fits into. Used specifically in filtering resources. Resources can have multiple tags, and tags can have multiple resources, but a resource does not need to be tagged, and a tag does not need to be associated with any resources.
