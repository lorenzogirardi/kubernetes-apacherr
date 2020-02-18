# kubernetes-apacherr  

## The semi-unuseful apache implementation in kubernetes  

Well , why we are talking about apache httpd in kubernetes ?  
We have ingress resources , we have ambassador and we are using microservices...  
True but internet was not built yesterday and for some reasons out of my knowledge ,   
people are ostinated to manage rewrite rules in apache instead to use a dedicated router application (react, zuul .. database!?!?! etc etc)  
However sometimes we have to balance between the academic vision and the reality.

## digression

Talking about apache https , nginx , haproxy ... i'm referring to the idea behind manage a complex website.  
A website could be composed my hundreds of microservices but the domain it's usually one     
www.example.com  

www.example.com has the root path /  
/it/ managed by cms  
/it/offerte managed by cms  
/uk/ managed by cms  
/uk/offers managed by cms  
/../ whatever   
/it/clienti/ managed by customer-app  
/uk/customers/ managed by customers-app  
/../somethingelse  
/secure/ managey by payment-app  
...  
omg path clash ... so we need to exclude in apache /uk/customers/ from cms proxypass but  
meantime enable a dedicated proxy pass to a specific application endpoint.  
and we are mannually manage all language , all applications with static configurations...  
and if tomorrow we will open APAC ... what we have to do ?  
and if we need to cover a former third parti company and acquire his seo ranking we should create  
thousands of redirects ? and how we can can validate avoiding loops ?  




## Some concepts about this project  
Even if we are working in a dynamic environment it's no rare to have the traditional layers

DMZ --> layer 1  
Application --> layer 2  
Database -->layer 3

In this picture apache httpd should usually placed on layer 1 ,   
but consider apache not for the common web server but like a "product" ,   
something that could be managed not by SRE , but Product Engeneer.  
A product that own a dedicated business, like seo, sem , vanity urls etc etc.  

Having those considerations, we can "downgrade" apache httpd in layer 2 like any application  
and honor the DMZ (if needed ?!?!) on top by ingress/haproxy/bigf5 (where maybe we can terminate the TLS).

