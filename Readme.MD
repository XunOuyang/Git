// From https://learngitbranching.js.org/
// https://backlog.com/git-tutorial/cn/stepup/stepup6_3.html

1. git branch [branchname]
Branch early, branch often.

```
git branch newImage
```
用以上命令先建立一个branch。
如果想要在branch上工作，必须要先git checkout branch。不然每次移动的还是master
如果是想要把已知节点变成一个branch
git branch [branchname] [nodename]

2. git checkout [branchname] 

if you want to create a new branch AND check it out at the same time, you can simply type 
```
git checkout -b [yourbranchname]
```

以上一句，相当于 git checkout [yourbranchname]; git commit


3. git merge [branchname]
如果想要把branch merge到master里面，一定要先checkout master，在master上了，再git merge branchname就行了。

4. git rebase 
如果已经在一个branch上了，然而master已经不是branch的祖先了，此时如果希望这个branch的改动都是基于另外一个节点，比如master，那么可以用
git rebase master [branchname]

5. relative commit
Moving upwards one commit at a time with ^
Moving upwards a number of times with ~<num>

Let's look at the Caret (^) operator first. Each time you append that to a ref name, you are telling Git to find the parent of the specified commit

6. git branche -f
One of the most common ways I use relative refs is to move branches around. You can directly reassign a branch to a commit with the -f option. So something like:

git branch -f master HEAD~3

moves (by force) the master branch to three parents behind HEAD.

7. git reset 
git reset [previousnode]， 这样当前的节点就会被删除掉了。并且指针指向previousnode.
git reset reverts changes by moving a branch reference backwards in time to an older commit. In this sense you can think of it as "rewriting history;" git reset will move a branch backwards as if the commit had never been made in the first place.

8. git revert
While resetting works great for local branches on your own machine, its method of "rewriting history" doesn't work for remote branches that others are using.

In order to reverse changes and share those reversed changes with others, we need to use git revert. Let's see it in action

9. git cherry-pick 
git cherry-pick C1 C3 C2
另开一个branch，选择之前想要的节点commit出来，而且顺序可以自定义

10. git rebase -i HEAD~[num]
直接调用GUI来做cherry-pick

11. git tag v1 C1

12. git remote:
git checkout origin/master; git commit

13. git fetch:
git fetch performs two main steps, and two main steps only. It:

downloads the commits that the remote has but are missing from our local repository, and...
updates where our remote branches point (for instance, o/master)
git fetch essentially brings our local representation of the remote repository into synchronization with what the actual remote repository looks like (right now).
git fetch, however, does not change anything about your local state. It will not update your master branch or change anything about how your file system looks right now.

This is important to understand because a lot of developers think that running git fetch will make their local work reflect the state of the remote. It may download all the necessary data to do that, but it does not actually change any of your local files. We will learn commands in later lessons to do just that.

so in other words, git fetch is just "download"

14. git pull
git pull = git fetch; git merge origin/master
git pull --rebase

15. git push
git pull相反，remote repository会跟local同步

4. git rebase 
