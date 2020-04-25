# Feature Backlog / Further Development 

Features yet to be implemented are detailed here.

## A Level (Critical)

### 1. Expiring Login Tokens:
* No expiry is set for currently logged in users 
* `An expiry token should be stored in the cookie`

<br>

## B Level (Non-essential, but impair the usability of the system)

### 1. Referral#create :: wait time 
* SMS and Email notifications are dispatched on the main thread, resulting in a long wait time before the server can render the returned page. 
* `Calls to the sendSMS and sendEmail referral model functions should be dispatched on separate threads`

<br>

## C Level (Nice to have)

### 1. Referral#create :: CaseLoad selector
* When selecting a user from the caseload, the `select` dropdown used is not scalable to many users.
* `Implement a search functionality `