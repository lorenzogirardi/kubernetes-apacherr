# kubernetes-apacherr  

## The semi-unuseful apache implementation in kubernetes  

Well , why we are talking about apache httpd in kubernetes ?  
We have ingress resources , we have ambassador and we are using microservices...  
True but internet was not built yesterday and for some reasons out of my knowledge ,   
people are ostinated to manage rewrite rules in apache instead to use a dedicated router application (react, zuul .. database!?!?! etc etc)  
However sometimes we have to balance between the academic vision and the reality.

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



