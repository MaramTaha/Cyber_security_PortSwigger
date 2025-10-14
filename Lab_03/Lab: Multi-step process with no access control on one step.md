# Lab: Multi-step process with no access control on one step 

# Objective 
* The vulnerability is that the website makes sure that only admin can change users roles but in the Confirmation step it doesn't check who are making this change .

# Solution 
* make an upgrade request as an admin and send this request to repeater to make changes using this request .
* login in as a user and copy user session cookies and past it in the admin request u have send to repeater and change user name .
### Steps
1. login as admin using admin credentials `administrator:admin`
1. Open burpsuite & inception
1. upgrade `Carlos` Role 
    * send this request to repeater
    *![pic](Lab_03\admin_request_before_edit.png)
1. login as a user using using the credentials `wiener:peter`
    * send this request to repeater
    * copy session cookies
    *![pic](Lab_03\wienet_request.png)
1. go to the upgrade role request that you have send to repeater before in step 3 
    * replace session cookies with cookies for `wiener` session that you have copied in step 4 
    * replace `carlos` with `wiener`
    * ![pic](Lab_03\admin_request _after_edit.png)
1. [pic](Lab_03\Lab_solved.png)
## References
* [Lab-Link](https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step)