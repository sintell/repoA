###01. create repo (repo A)
- mkdir repoA
- cd repoA/
- git init

###02. repo A: create 1st commit with some files (file A, file B)
- echo "This is file A" >> file.A
- echo "This is file B" >> file.B
- git add file.A file.B
- git commit -m "First commit"

###03. repo A: create branch branch1 from master
- git branch branch1

###04. clone the current repo (repo B)
- cd ..
- git clone repoA repoB
- cd repoB

###05. repo B, branch1: create 2nd commit containing new file (file C)
- git co branch1 
- echo "This is file C" >> file.C
- git add file.C
- git commit -m "Added file.C"

###06. repo B: push changes to repo A
- git push -u origin

###07. repo A, branch1: modify line#1 in file C and commit
- cd ../repoA
- git co branch1 
- echo "This is file C from repo A" >> file.C
- git add file.C
- git commit -m "Updated file.C"

###08. repo B, branch1: modify line#1 in file C and commit
- cd ../repoB
- echo "This is file C from repo B" >> file.C
- git add file.C
- git commit -m "Updated file.C"

###09. repo B, branch1: fetch changes from repo A
- git fetch ../repoA
- git st
- git fetch ../repoA

###10. repo B, branch1: merge in repoA's branch1 (resolve conflict)
- git merge FETCH_HEAD 
- vi file.C
- git add file.C
- git commit -m "Merged with repoA"

###11. repo A: add repoB as new remote
- cd ../repoA
- git remote add ../repoB
- git remote add origin ../repoB

###12. repo A, branch1: merge in repoB's branch1
- git st
- git fetch origin 
- git merge origin/branch1
