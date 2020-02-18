# kubernetes-apacherr  

## The semi-unuseful apache implementation in kubernetes  

Well , why we are talking about apache httpd in kubernetes ?  
We have ingress resources , we have ambassador and we are using microservices...  
True but internet was not built yesterday and for some reasons out of my knowledge ,   
people are ostinated to manage rewrite rules in apache instead to use a dedicated router application (react, zuul .. database!?!?! etc etc)  
However sometimes we have to balance between the academic vision and the reality.

