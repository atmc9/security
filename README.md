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
