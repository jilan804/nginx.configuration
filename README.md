**STEP1**:
# nginx.configuration

select new item ----> select pipeline job -----------> take a sample pipeline syntax(inside of given git repo) ------->use snippetGenerator --->Generate pipeline script 
------->output of syntax given is shell module


**STEP2**:
automatically trigger to use of webhook:
----------------------------------------
*)go to setting select the webhook option and add the http://52.66.195.107:8080/github-webhook same way jenkins UI select the GIThubhook trigger for GITscm polling  


**step3**:
install the nginx with help of ansible playbook:
-----------------------------------------------
---
 - name: install the nginx
   hosts: localhost
   become: yes
   tasks:
     - name: ensure nginx is at the latest version
       apt: name=nginx state=latest
     - name: start nginx
       service:
         name: nginx
         state: started
         
**step4**:
passwordless setup jenkins user:-
--------------------------------
 cd /etc/sudoers.d/
 vi 90-cloud-init-users
 ubuntu ALL=(ALL) NOPASSWD:ALL
jenkins ALL=(ALL) NOPASSWD:ALL
:wq!---------->save it 
**====================================congrats your setup done with cicd pipeline ==================================**


