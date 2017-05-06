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

