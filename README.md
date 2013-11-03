 mkdir repoA
 cd repoA/
 git init
 echo "This is file A" >> file.A
 echo "This is file B" >> file.B
 git add file.A file.B
 git commit -m "First commit"
 git branch branch1
 cd ..
 git clone repoA repoB
 cd repoB
 git co branch1 
 echo "This is file C" >> file.C
 git add file.C
 git commit -m "Added file.C"
 git push -u origin
 cd ../repoA
 git co branch1 
 echo "This is file C from repo A" >> file.C
 git add file.C
 git commit -m "Updated file.C"
 cd ../repoB
 echo "This is file C from repo B" >> file.C
 git add file.C
 git commit -m "Updated file.C"
 git fetch ../repoA
 git st
 git fetch ../repoA
 git merge FETCH_HEAD 
 vi file.C
 git add file.C
 git commit -m "Merged with repoA"
 cd ../repoA
 git remote add ../repoB
 git remote add origin ../repoB
 git st
 git fetch origin 
 git merge origin/branch1 
