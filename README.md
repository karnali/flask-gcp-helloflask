# flask-gcp-helloflask
Continuous Delivery of Flask Application on Google Cloud Platform (GCP). Build a web app using Python’s Flask and Google App Engine in Google Cloud Platform (GCP) using GCP Cloud Shell environment.
We will then push source code to Github.   Configure Cloud Build to Deploy Changes on build.  


# Steps involved 
- Create project in GCP: flask-gcp-helloflask.
- Flask app: Clone the hello world sample app repo. 
- Github. 

# GCP
1. Create Project in GCP - flask-gcp-helloflask  
![Image](../master/images/Picture1.png?raw=true)

2. Activate cloud shell

3. List project
$ gcloud config list project
[core]
project = flask-gcp-helloflask
Your active configuration is:

3. Describe Project
$ gcloud projects describe $GOOGLE_CLOUD_PROJECT

4. verify you are working on correct project and if not then switch:
$ gcloud config set project $GOOGLE_CLOUD_PROJECT

5. Create app engine using cloud shell.I will chose us-east1 region.
$ gcloud app create
please enter your numeric choice:  13
Creating App Engine application in project [flask-gcp-helloflask] and region [us-east1]....done.
Success! The app is now created. Please use `gcloud app deploy` to deploy your first app.

6. Clone the hello world sample app repo.
$ git clone https://github.com/GoogleCloudPlatform/python-docs-samples
Cloning into 'python-docs-samples'...

7. Change directory to 
$ cd python-docs-samples/appengine/standard_python37/hello_world
$ tree
.
├── app.yaml
├── main.py
├── main_test.py
└── requirements.txt

8. Create and source the virtual environment:
$ virtualenv --python $(which python) venv
$ source venv/bin/activate

9. Install Flask - Now pip is installed requirements.txt says install Flask==1.x.x
```
$ pip install -r requirements.txt
Successfully installed Flask-1.1.1 Jinja2-2.11.1 MarkupSafe-1.1.1 Werkzeug-0.16.1 click-7.0 itsdangerous-1.1.0
```
10. Run flask locally in gcp shell
```
$ python main.py  
![Image](../master/images/Picture4.png?raw=true)  
```

11. Deploy and run Hello World on App Engine
```
$ gcloud app deploy  
```
![Image](../master/images/Picture2.png?raw=true)  

```
12. $ gcloud app browse

https://flask-gcp-helloflask.appspot.com

Congratulations! You've deployed your first Python 3.7 app to App Engine standard environment!  
```
![Image](../master/images/Picture5.png?raw=true)

```
13. $ gcloud app instances list
SERVICE  VERSION          ID                                                                      VM_STATUS  DEBUG_MODE
default  20200130t180731  00c61b117ca347ac9853f4ddb72b6284b43c5c9fcf37baec54f999f7b746ac09d9a896  N/A

14.$ gcloud app versions list
SERVICE  VERSION.ID       TRAFFIC_SPLIT  LAST_DEPLOYED              SERVING_STATUS
default  20200130t180731  1.00           2020-01-30T18:08:35-05:00  SERVING

15. $ gcloud app describe
authDomain: gmail.com
codeBucket: staging.flask-gcp-helloflask.appspot.com
defaultBucket: flask-gcp-helloflask.appspot.com
defaultHostname: flask-gcp-helloflask.appspot.com
featureSettings:
  splitHealthChecks: true
  useContainerOptimizedOs: true
gcrDomain: us.gcr.io
id: flask-gcp-helloflask
locationId: us-east1
name: apps/flask-gcp-helloflask
servingStatus: SERVING  
![Image](../master/images/Picture6.png?raw=true)  
```
# Clean up
To avoid incurring charges, you can delete your Cloud project to stop billing for all the resources used within that project.
1. In the Cloud Console, go to the Manage resources page. https://console.cloud.google.com/
2. In the project list, select the project that you want to delete and then click Delete
3. In the dialog, type the project ID and then click Shut down to delete the project. 




# GitHub Instructions!

# Adding an existing project (local) to GitHub using the command line

1. Create a new repository on GitHub.com. To avoid errors, do not initialize the new repository with README, license, or gitignore files. You can add these files after your project has been pushed to GitHub.

2. Open Terminal Change the current working directory to your local project. config-globals.
Set the username and email address for your Git commits. Replace [EMAIL_ADDRESS] with your Git email address. Replace [USERNAME] with your Git username.

```
$ git config --global user.name "First Last"
$ git config --global user.email "email@domain.com"
```
3. Generate rsa key locally.
```
$ ssh-keygen -t rsa
$ cat /home/admin_/.ssh/id_rsa.pub 
```
4. Copy .pub key and go to github and create SSH keys under settings.

5. Create a new repository on the command line.  Add, commit, and push the files.
```
$ echo "# flask-gcp-helloflask" >> README.md
$ git init
   Initialized empty Git repository in /home/admin_/python-docs-samples/appengine/standard_python37/hello_world/.git/
$ git add README.md
$ git commit -m "first commit"
[master (root-commit) a6ed6b2] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

nothing added to commit but untracked files present (use "git add" to track)
$ git remote add origin git@github.com:karnali/flask-gcp-helloflask.git
$ git push -u origin master
   ****[You will see Permission denied (publickey) if you don't have ssh setup].***
Counting objects: 3, done.
Writing objects: 100% (3/3), 231 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:karnali/flask-gcp-helloflask.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
```

6. add $ touch .gitignore locally copy paste .gitgnore from template

7. Push all
```
$ git add .
$ git commit -m "First commit"
$ git push -u origin master
```


# push an existing repository from the command line
```
git remote add origin git@github.com:karnali/flask-gcp-helloflask.git
git push -u origin master
```

# Pull command to ‘pull’ down the README file onto the local folder
```
$ git pull origin master
```

# Delete files/folder in your local clone, commit that change to your local repository, and then push that 
change to the remote repository on GitHub.
```
$ git rm -r deploy.yaml
rm 'deploy.yaml'
```
```
$ git commit -m "remove unwanted files/folder"
[master 4140887] remove unwanted files/folder
 1 file changed, 4 deletions(-)
 delete mode 100644 deploy.yaml
```
```
$ git push origin master
Counting objects: 2, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 235 bytes | 0 bytes/s, done.
Total 2 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:karnali/flask-gcp-helloflask.git
   9b5d1dd..4140887  master -> master
$ ls -l
total 20
-rw-r--r-- 1 admin_ admin_   18 Jan 30 13:37 app.yaml
-rw-r--r-- 1 admin_ admin_  320 Jan 30 15:42 main.py
-rw-r--r-- 1 admin_ admin_  380 Jan 30 15:28 README.md
-rw-r--r-- 1 admin_ admin_   13 Jan 30 16:02 requirements.txt
drwxr-xr-x 6 admin_ admin_ 4096 Jan 30 13:49 venv
```

# If git pull from github fails
```
$ git reset --hard
$ git pull
```
# Modify main.py watch Cloud Build auto trigger build while git commit!!!

https://flask-gcp-helloflask.appspot.com/
```
$ git add .
$ git commit -m "build while git commit!!!"
$ git push
```


