```
tFile.txt
git add .
git config --global user.name "Aliaksandr Buhlayou"
git config --global user.email abuhlayou@elinext.com
git commit -m "1stFile added"
git log --oneline

#1767b7f 1stFile added
#22dc452 Initial commit

date > 2ndFile.txt
git add .
git status


# On branch master
# Your branch is ahead of 'origin/master' by 1 commit.
#   (use "git push" to publish your local commits)
#
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       new file:   2ndFile.txt

git commit -m "2ndFile added"
git log --oneline

#8759056 2ndFile added
#1767b7f 1stFile added
#22dc452 Initial commit

git checkout -b "dev"
git status

# On branch dev
# nothing to commit, working directory clean

date > 1stFile.txt
git add .
git commit -m "1st commit from dev"
date > 2ndFile.txt
git add .
git commit -m "2nd commit from dev"
git log --oneline

#bfb2421 2nd commit from dev
#43d95ad 1st commit from dev
#8759056 2ndFile added
#1767b7f 1stFile added
#22dc452 Initial commit

git checkout -b "features/do_one"
date > 1stFile.txt
git add .
git commit -m "commit from features/do_one"
git log --oneline

git checkout dev
date > 1stFile.txt
git add .
git commit -m "commit from dev 1 again"
date > 2ndFile.txt
git add .
git commit -m "commit from dev 2 again"
git log --oneline

git checkout master
date > 1stFile.txt
git add .
git commit -m "commit from master 1 again"
date > 2ndFile.txt
git add .
git commit -m "commit from master 2 again"
git log --oneline

#95ba182 commit from master 2 again
#1b808fe commit from master 1 again
#8759056 2ndFile added
#1767b7f 1stFile added
#22dc452 Initial commit

git checkout -b "hotfix/we_gonna_die"
git status
date > 3rdFile.txt
git add .
git commit -m "commit from hotfix" 

git checkout master
date > 1stFile.txt
git add .
git commit -m "commit from master again 3"
date > 2ndFile.txt
git add .
git commit -m "commit from master again 3"
git log --oneline

#af1fdcb commit from master again 4
#48c3445 commit from master again 3
#95ba182 commit from master 2 again
#1b808fe commit from master 1 again
#8759056 2ndFile added
#1767b7f 1stFile added
#22dc452 Initial commit

#Here starts 1.10
git merge dev
#error: 'merge' is not possible because you have unmerged files.
git add .
git commit -m "merge dev"
git merge dev
#Already up-to-date.

git merge features/do_one
#Auto-merging 1stFile.txt
#CONFLICT (content): Merge conflict in 1stFile.txt
#Automatic merge failed; fix conflicts and then commit the result.
git add .
git commit -m "merge features"
#[master ba466e1] merge features
git merge features/do_one
#Already up-to-date.

git log --oneline
#ba466e1 merge features
#3fa0d3c merge dev
#af1fdcb commit from master again 4
#48c3445 commit from master again 3
#95ba182 commit from master 2 again
#1b808fe commit from master 1 again
#4e0312c commit from dev 2 again
#e2ac0ff commit from dev 1 again
#6b380dc commit from features/do_one
#bfb2421 2nd commit from dev
#43d95ad 1st commit from dev
#8759056 2ndFile added
#1767b7f 1stFile added
#22dc452 Initial commit

git merge hotfix/we_gonna_die
#Merge made by the 'recursive' strategy.
# 3rdFile.txt | 1 +
# 1 file changed, 1 insertion(+)
# create mode 100644 3rdFile.txt

git checkout dev
git merge hotfix/we_gonna_die

#Auto-merging 2ndFile.txt
#CONFLICT (content): Merge conflict in 2ndFile.txt
#Auto-merging 1stFile.txt
#CONFLICT (content): Merge conflict in 1stFile.txt
#Automatic merge failed; fix conflicts and then commit the result.

git add .
git commit -m "merge hotfix to dev"
#[dev 7a5513d] merge hotfix to dev
git merge hotfix/we_gonna_die
#Already up-to-date.

git checkout features/do_one
git merge hotfix/we_gonna_die

#Auto-merging 2ndFile.txt
#CONFLICT (content): Merge conflict in 2ndFile.txt
#Auto-merging 1stFile.txt
#CONFLICT (content): Merge conflict in 1stFile.txt
#Automatic merge failed; fix conflicts and then commit the result.

git commit -m "merge hotfix to features"
#[features/do_one 586c5ac] merge hotfix to features
git log --oneline
git merge hotfix/we_gonna_die
#Already up-to-date.
```
