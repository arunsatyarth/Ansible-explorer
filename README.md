# Ansible-explorer
A solution which helps to view the complete flow of execution of ansible playbooks in a clean UI. 

- Execution is shown as a tree of tasks which can be expanded and collapsed to look at actual details.
- For each tasks it also shows, the invocation parameters and responses which makes it easy to understand what happened.
- Substeps can be toggled to show or hide which helps concentrate on important steps which matter.
- Filters are available to filter out unnecasary tasks like set_task  etc again to hide clutter.

# Background
If you are here, you would already know about Ansible. You might also have a codebase which has several playbooks either written by you or inherited from soneone. Either way, it has become a mess to read the code and figure out what is happening. If you are like me, you would have tried looking for a tool which shows a graphical representation of the code which would help to identify what the playbook tries to do. And that search might have brought you here.   

There are 2 ways to solve this problem. 
1. Static analysis (Parsing code files)
2. Dynamic analysis (Execute playbook and collect dumps)

## Issues with static Analysis
Ansible is a very dynamic tool. It can make decicions on which branches of tasks to execute based on values retreived at runtime. Hence by statically parsing the code, it is not possible to judge the flow of execution. 
However, if you have a small codebase and use very minimalistic features in ansible(eg; without looping etc) chances are this solution might work. 
If interested, you can check out https://github.com/haidaraM/ansible-playbook-grapher on github  which is a static analysis solution. Howver the layout it gives you is a graph of tasks rather than the flow of execution.
Some examples where the static analysis breaks are.
1. If you have files getting included based on jinja variables
   include_task  /path/{{filename}}
2. Files being included in a loop using with_items

# How Ansible-explorer works
This is a dynamic analysis solution where a playbook has to be executed and certain dumps collected, which is then is used for generating the tree. Checkout the below screenshots of the UI it gives you.

Execution Flow
![Running View](https://github.com/arunsatyarth/Ansible-explorer/blob/main/img/4.PNG)

Toggle buttons to view Params, Response etc
![Running View](https://github.com/arunsatyarth/Ansible-explorer/blob/main/img/3.PNG)

# How to use
Currently, this solution needs some guidene to setup and hence is only available on demand. Get in touch with me at arun.satyarth@gmail.com and I will help with setting it up. Its a one time setup after which it can be operated without any overseeing. 

