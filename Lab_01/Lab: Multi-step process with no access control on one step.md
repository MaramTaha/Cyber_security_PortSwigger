# Lab URL-based access control can be circumvented

### Objective 
* Take admin role and delete user `carlos`

### Solution 
* We can't load Admin page and the back-end application is built on a framework that supports the [X-Original-URL](#x-original-url) header. 
#### Steps
1. open burpsuite and open intercept 
1. go to /admin 
    * it will show `Access denied` message
1. send /admin request to repeater 
1. change request line to `GET / HTTP/2`
    * this means 
        * methode -> Get
        * path -> / (Root)
        * protocol -> HTTP
        * version -> 2
1. write `X-Original-Url: /admin`
    * this means 
        * the original url was `/admin` 
        * ![pic](Lab_01\Admin_Request.png)
1. now request is ready to send and admin page will open 
1. on website click delete `carlos` and send the request to repeater 
1. make step 4 in the delete request
1. write X-Original-Url: /admin/delete 
    * ![pic](Lab_01\delete_carlos_request.png)

* ![pic](Lab_01\Lab_solved.png)

## References
* [X-Original-URL](https://medium.com/@cirilptomass/x-original-url-a-loophole-that-could-expose-your-web-app-71b050d6d07d)

* [Lab_Link](https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented)
### X-Original-URL
* The `X-Original-URL` HTTP header is used by reverse proxies (such as Nginx, Apache, or load balancers) to preserve the original requested URL before internal rewriting or redirection. It helps backend applications determine the original request when URL rewriting is in use.