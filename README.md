The world is moving towards a Gitops methodology, so while playing around with Keycloak/RHSSO  
I've found out there is a way to pull the configuration files from a git repo.  

There are only few documentations about it and non of them are detailed enough in my opinion,   
1 - https://www.wildfly.org/news/2018/09/28/Git-History/  
2- https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/7.2/html/configuration_guide/jboss_eap_management#using_git_to_manage_configuration_data  
3- https://access.redhat.com/solutions/3943361  
  
I had problems configuring it to work properly, so I decided do document my steps.  
This process is really simple, and it should only be done once.

1. Create the remote repo and clone it to a local directory.
2. Copy the content of Keyclaok's standalone folder to the local directory you've created earlier.
3. Copy the .gitignore content from this repo to your local .gitignore file and push it so the remote repo will be updated will all of the needed files.
4. On every 
