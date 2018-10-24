# Index

#### Commit to Repository
* git add -A
* git commit -m 'Commit Message'
* git push origin master

#### Create Local Repository + Connect to Remote
* git init
* touch test.py
* git add -A
* git commit -m 'Commit Message'
* git remote add origin https://github.com/john-b-yang/test.git
* git push origin master

#### Copy Existing Repository + Test Commit
* git clone https://github.com/john-b-yang/test.git
* cd test
* touch test.py
* git add -A
* git commit -m 'Commit Message'
* git push origin master

#### Merge a branch into Master 
Given local branches 'test' and 'master'
* git checkout master
* git pull origin master
* git merge test
* git push origin master

#### Miscellaneous
* git blame test.py
* git log
* git status
