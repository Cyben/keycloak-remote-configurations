# Keycloak in a gitops glance 
The world is moving towards a Gitops methodology, so while playing around with Keycloak/RHSSO  
I've found out there is a way to pull the configuration files from a git repo. 

There are only few documentations about it and non of them are detailed enough in my opinion :(,   
1 - https://www.wildfly.org/news/2018/09/28/Git-History/  
2- https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/7.2/html/configuration_guide/jboss_eap_management#using_git_to_manage_configuration_data  
3- https://access.redhat.com/solutions/3943361  
  
## The real deal
I had problems configuring it to work properly, so I decided do document my steps.  
This process is really simple, and it should only be done once.

1. Create the remote repo and clone it to a local directory.
2. Copy the content of Keyclaok's standalone folder to the local directory you've created earlier.
3. Copy the .gitignore content from this repo to your local .gitignore file and push it so the remote repo will be updated will all of the needed files.
4. Now just start your standalone[-ha] node with the command:
```
./standalone.[sh|bat] --git-repo=http[s]://<link-to-remote-git-repository>/<user>/<repository>.git --git-branch=main
```

> It is important to add `--git-branch=main` as the default branch is outdated and it is still configured as 'master'  
  
<br />  
<br />  
  
~~~
* This was tested on a 'public repo', when using a 'private repo' you will need to configure an Elytron configuration file  
* I couldn't really get it to work properly, pushing configuration from the server to the git repo didn't work for me and there is lack of documentation about troubleshooting this kind of things (In a way it could be more 'gitops forward' because the only way to change the configuration would be by hand)
