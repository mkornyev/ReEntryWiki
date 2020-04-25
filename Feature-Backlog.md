# Feature Backlog / Further Development 

Features yet to be implemented are detailed here.

## A Level (Critical)

### 1. Expiring Login Tokens
* No expiry is set for currently logged in users 
* `An expiry token should be stored in the cookie`

### 2. Hard coded URLs 
* The SMS and Email templates use hard-coded application paths for links. 

<br>

## B Level (Usability Impairing)

### 1. Referral#create :: wait time 
* SMS and Email notifications are dispatched on the main thread, resulting in a long wait time before the server can render the returned page. 
* `Calls to the sendSMS and sendEmail referral model functions should be dispatched on separate threads`

<br>

## C Level (Nice to have)

### 1. Referral#create :: CaseLoad selector
* When selecting a user from the caseload, the `select` dropdown used is not scalable to many users.
* `Implement search functionality`

### 2. Resource#create/edit :: Tag checkboxes
* The checkbox list isn't scalable to many tags.
* `Use a beter selector`

### 3. Resource#edit :: Images 
* Images cannot be removed once added to a resource.
* `Use an ImageField and override the entire image upload mechanism` OR `add a link (with a remove image action) to the resource form`