# Running multiple Redis on one server

I am trying to run two instances of Redis on a single machine, setting them up
with different ports via ANsible 1.3, but have hit a problem.  The group variables
are not being picked up the way I think they should be.

group_vars/redis_ghost.yml and group_vars/redis_logstash.yml set the 'name' and 'port' 
for each service I want to run, but it looks like they are not being picked up
perperly for each play.

Demonstration:

$ ansible-playbook -i experiment redis_service.yml

    PLAY [redis - install] ******************************************************** 
    
    GATHERING FACTS *************************************************************** 
    ok: [localhost]
    
    TASK: [redis - Install redis] ************************************************* 
    ok: [localhost] => {"item": "", "msg": "Installing redis"}
    
    PLAY [redis - ghost service] ************************************************** 
    
    TASK: [redis service - debug] ************************************************* 
    ok: [localhost] => {"item": "", "msg": "set up redis service logstash on port 6379"}
    
    PLAY [redis - logstash service] *********************************************** 
    
    TASK: [redis service - debug] ************************************************* 
    ok: [localhost] => {"item": "", "msg": "set up redis service logstash on port 6379"}
    
    PLAY RECAP ******************************************************************** 
    localhost                  : ok=4    changed=0    unreachable=0    failed=0   
    
