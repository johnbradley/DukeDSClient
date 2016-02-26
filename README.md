# DukeDSClient
Command line tool to upload/manage project on the [duke-data-service](https://github.com/Duke-Translational-Bioinformatics/duke-data-service).

###Install:
```
git clone https://github.com/Duke-GCB/DukeDSClient.git
cd DukeDSClient
python setup.py install
```

### Additional Setup:
To use DukeDSClient, you must supply an authentication token.
This requires a [Duke NetID](https://oit.duke.edu/email-accounts/netid/).
This token identifies you with the service, and can be generated by visiting the [Duke Data Service API Explorer](https://uatest.dataservice.duke.edu/apiexplorer).
Click the Authenticate button.
Click Duke Authentication Service.
Enter your NetId credentials.
Your authentication token will then be printed at the top of the screen.

Note that tokens obtained this way are only valid for 2 hours. 
Work is underway to improve this process and obtain longer-lived tokens.
```
export DUKE_DATA_SERVICE_AUTH='...'
```
###Use:
See general help screen:
```
ddsclient -h
```
See help screen for a particular command:
```
ddsclient <command> -h
```

All commands take the form:
```
ddsclient <command> <arguments...>
```

###Upload:
```
ddsclient upload -p <ProjectName> <Folders/Files...>
```

This will create a project with the name ProjectName in the duke data service for your user if one doesn't exist.
It will then upload the Folders and it's contents to that project.
Any items that already exist with the same hash will not be uploaded.


Example: Upload a folder named 'results' to new or existing project named 'Analyzed Mouse RNA':
```
ddsclient upload -p 'Analyzed Mouse RNA' results
```

###Add User To Project:
```
ddsclient add_user -p <ProjectName> -u <UserFullName> --auth_role 'project_admin'
```
Example: Grant permission to user named 'John Bradley' for a project named ''Analyzed Mouse RNA' with default permissions:
```
ddsclient add_user -p 'Analyzed Mouse RNA' -u 'John Bradley'
```

###Testing:
From the root directory run the following:
```
python setup.py test
```
