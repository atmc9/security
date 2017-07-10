# security

* **SSL (Secure Socket Layer)** - Recommented to use SSL to be safe from men in middle attacks.

* **HSTS (HTTP strict Transport Security)** - HSTS Header   - can be added from nWebSec nuget package. (Way to tell browser to always call in SSL mode)

* **SQL Injection** - "select * from customers where name={a}"   if a is input paramter of "anvesh; drop table customers;" 

* **CSRF (Cross Site Request Forgery)** - If I login to a site(bankofAmerica) my cookie is set in my browser. If I got a fake page with
    
    ```
    you got 1000$
    <Form action="https://bankofAmerica.com/api/tranfer" method ="post">
      <input type="hidden" name="amount" value="1000000"/>
      <input type="hidden" name="AccountNumber" value="INTRUDERSACCOUNT" />
      <input type="submit" value="Click here to redeem!.">
    </Form>
    ```
    .Net core has asp-antiforgery as a solution which generates a hidden field _requestValidationToken
    
* **XSS (Cross site Scripting)** - Attacker places Javascript into webpage, allows attackers to access to everything in the broswer. Solution is to Encode all html inputs, MVC automatically encodes all variables. For input query string use Server.UrlEncode().

* **CSP (Content Security Policy)** - Disable inline javascipt, WhiteList URLS that are ok to get javasciprt from. We can set the defaultSources as self and can add custom sources like "maxcdn.bootstrap.com" 
    
* **Open Redirection Attack** - If I got the link "http://bank.com/account/Login?returnURL=http://bank.net/account/Login" once the user login to the bank.com site he will be redirected to bank.net with the message showing the password is wrong. The user gives his username and password, which are in hands of hacker.  We can solve this by checking for URl.IsLocalUrl(returnURL);

* **Click-jacking** - The attacker can pull bank.com on Iframe on his won site and places a button "claim your 100000$" button that exactly sites on top of tranfer button.  Avoided by adding "X-Frame-Options: Deny/Sameorigin"


In traditional ASP.net applications, whne the user login cookie will be saved to browser and used for subsequent calls. The cookie info is generated by Encrypted data and its Hash are send, upon return Encrypted data is again Hashed and compared with original Hash to veirify nothing is tampered. Machine key is used for the symetric encryption. 
Disavantages: No key rotation, no Key protection, required to sync them on a Web farm, If that key is stolen we will be in trouble.
## .NetCore Security:  
   No more Machine key system. 
   * ** Data Protection API** - Key per application, Ket rotation - default 90 days.
   
   
  Some good reads: http://robertheaton.com/2014/03/27/how-does-https-actually-work/
  
  How CORS work: https://www.html5rocks.com/en/tutorials/cors/
  https://en.wikipedia.org/wiki/Cross-origin_resource_sharing
  
  ![CORS Server FlowChar](https://www.html5rocks.com/static/images/cors_server_flowchart.png)
  
  ![CORS FlowChar](https://en.wikipedia.org/wiki/File:Flowchart_showing_Simple_and_Preflight_XHR.svg)
  

