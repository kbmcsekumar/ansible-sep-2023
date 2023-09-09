## Installing Ansible Tower opensource
https://medium.com/@jegan_50867/installing-ansible-tower-awx-e46d5231357d

## Ansible Tower
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/0a49134f-6cec-488b-844f-4b449bd1cd45)


## What is AWX ?
- is the opensource Ansible Tower
- this supports Web Interface
- we can't develop ansible playbook in AWX
- already existing playbook we can import the playbook from GitHub or some version control as Projects
- benefits
  - we don't need to install ansible locally to run the playbook
  - user management is possible in AWX
  - you could create multiple users with different access and add to teams
  - it is possible which team members can view/execute which playbook
  - you can check the history playbook execution logs
  - you can access Ansible AWX Web console from any remote machine using normal web browsers without needing to install any software locally
- drawbacks
  - in case you face any technical challenge, you won't any support from Red Hat/IBM
  - only community support you would, this might take take to get a response, or you may not any reponse at all
  - you are on your own in case no response comes from the community


## What is Red Hat Ansible Tower ?
- this is an enterprise product from Red Hat
- developed on top of opensource AWX
- hence, supports all the features of AWX within Red Hat Ansible Tower
- benefits
  - you get world-wide support from Red Hat (an IBM company)
  - Web console
  - no need to install ansible locally to execute playbooks
  - Ansible is available to you over web browser
  - Many teams can use the same Ansible Tower organization wide
- drawbacks
  - can't develop playbook with Ansible Tower


## Demo - Ansible Tower Demo

Red Hat Ansible Tower Dashboard looks like as shown below
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/8e0cb2d5-8b15-4682-b6a3-f6ee6b7a214f)

### Creating a Project in Ansible Tower
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/db8d9d0f-61a8-4303-80b8-722cee8cf269)

Click on Add
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/1d2055eb-0dab-460f-a408-5e685352b6fb)

Click on Save
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/e543bde3-a047-4646-a20b-5920f1bb4807)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/67f0db0c-2721-42f2-816b-720e98273cff)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/21816373-c4ae-4473-96fd-723038e5f8fd)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/3bca1ff6-95a0-46ca-a08c-a88906d6e846)

### We need create an inventory
Navigate Resources --> Inventory
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/e0941f88-f9cb-4051-9def-74b675448c6c)

Click on Add --> Add Inventory
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/a1f2f328-e3a3-40d4-bf81-72dbb5ee0e7d)
The number of hosts you have automated against is below your subscription count.
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/e8469265-3ccb-4717-ba37-5dd75c2e33ef)

Click on Save
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/f8b943c3-e716-4a5e-8f27-48c8672c9a66)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/bdf4a052-a2c2-4ff2-942f-e8057ba6cebb)

Click on Hosts Tab
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/e1e49b2d-348b-4c0e-b87f-f0dd3a2f2781)

Click on Add
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/5e182c0f-9b1a-407f-84ee-f6a880495f6f)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/c159a08d-25d0-4695-b1e2-15be3a8df879)

Repeat this process for Ubuntu2, CentOS1 and CentOS2 Containers
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/cb17e186-a59a-4251-ac9e-2aa3e4eeca09)

Click on Save
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/c5c90369-50a8-4b82-8acb-871aeb5d3881)
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/c6e03b0c-cc86-4335-b7f1-1d8a9e0265d3)
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/60bcc91f-08d3-407b-a36c-7bb6bd69c45b)

click on Add
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/6a2b779e-cb13-4509-9cd1-c5185d49d982)
Click on Save
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/e3c2fc78-6932-4dba-8107-4b9f54a6ce2a)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/6003638e-fe84-4408-9413-ede47dc1e257)
Click on Add
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/b01b1ded-cefb-4836-aa53-1a195dc6912d)
Click on Save
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/3ae10701-d86d-4c16-a1c0-fd37474c43e5)

We are now done with the inventory creation
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/adbbe236-8e1c-4ffc-8bd1-55f2b4f28a96)


For the add your lab machine private key, we need to navigate to Resources --> Credentials menu on the left side of Ansible Tower
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/40194653-d8dd-468b-8572-613f4acc9d53)

Click on Add
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/c25f7df4-354e-4b3e-89f1-51fba7bca94a)

Copy the private key you generated while buiding the custom docker image
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/b21a364d-01b2-4ad5-b7d8-6cadb922eef2)
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/18644704-891e-4924-878f-9238fe9af180)

Paste
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/b2bb9a65-5294-4ae2-b174-682964f7140e)
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/b1104c61-1b4b-4403-9319-a3129fbcf39e)
Click on Save
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/1821b536-9c26-4be0-bdcc-4e6bfcd9d637)


### We need to create the Job Template

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/7cc79728-c1e4-4ba4-becc-406e06874f71)

Click on Add --> Add Job Template
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/6c83bd91-b72e-4535-9c3e-47b552630d65)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/f7f40157-850b-443f-88aa-4fda28085043)

Select the Inventory we created in the previous steps and click on select
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/6544fc96-5d83-4972-94b0-bd30d53135f7)

Select the Project we created in the previous steps and click on select
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/fbe0231f-c826-4c4e-a2c4-19de3c8e6da6)

Notice, the playbooks from the TekTutor Training Repository are listed
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/cdf396fb-a034-4a1b-bdd7-4a5e806db963)

Select the playbook you wish to run
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/29acccf3-e20a-44d5-9f7a-5c589d1f2795)

Select the Credentials
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/d7c3d0b9-a681-4782-8ca0-030b4e4f91d9)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/9df6d6a3-2e6f-4ba9-ab22-bf8881e0e61b)

Click on Save button
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/c8eb68fc-3154-4e3f-b7e7-8c9edf4bd3aa)

Job Template is created successfully now
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/6d6bc149-0c06-41ac-b885-26d5beb798ce)
The number of hosts you have automated against is below your subscription count.
To run the playbook, click on the Launch button
![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/c52373b9-90c2-4e59-94cd-d05ace37994a)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/a88e4501-1e93-4df5-a14a-5b233fe68d07)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/dfef5263-e957-4cbe-b85a-212ed910244e)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/19854ed0-2cdf-44ed-bca1-dbac9e80e0ff)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/6ccc8d04-94ec-47f3-8249-c8704638579c)

![image](https://github.com/tektutor/ansible-aug-2023/assets/12674043/26276e43-4bd3-43a1-9e93-f30fda8a3fc5)


## Post Test Url
https://app.mymapit.in/code4/tiny/ZMlZNR
 
## Feedback link
https://tcheck.co/HgKc9b
