# Git and Github

## Example Task

- Go to github, add new empty public repo (Learn-Github).
- open your local project (html) using VS code

```bash
git init
echo "# Learn Github" > README.md
git add .
git commit -m "initail commit"
git branch -M main
git remote add origin https://github.com/engchamitha/Learn-Github.git
git push -u origin main
git status
```

- Now Lets make some branches. From here, We do not commit anything to main branch.
- We can make the branches in remote repo or local repo. Doesn't matter.
- Option 1: make the branch in remote repo

```bash
Go to Github, open the repo, click branches, new branch, Give the name Styling branch.
Sourse is so importent. It means, starting from which branch, this new branch seperate.
So usually we can merge back to that sourse branch after doing our changes.
This branches are in remote repo, So we need to update these infomation to the local repo. In the local terminal type;

git fetch --all
Now Locat repo has all the updates in the remote repo. Only the updates. So you need to create a local branch manually that tracks the remote branch.

git checkout Styling-branch
```

- Option 2: make the branches in local repo

```bash
Lets use GitDesktop to make branch. Styling branch
Then publish this branch to Github
```

- Make Styling-branch as the working branch and make a style.css file. Then link that to index.html file.
- Then commit it. You can use Github Desktop. Add a meaningful description. Still that commit is in local repo.
- Then push that commit to remote repo.
- Go to Github. You can see the notification of a pull request. It means, style.css file is still in Styling branch. So we need to request to merge our changes to main branch from the owner of the project. After we request, he will review it and merge our change to main branch.

```bash
Go to Github Desktop  click the preview pull request. Then click create pull request.
It will open Github and you can see the pull request application.
Add a meaningfull description. And create pull request.
In the conversation, you can see the all the details.
In the Files Changed tab, you can see all the changes in files.
From the settings, change the Diff view to split, so you can clearly see how the files have been changed.
Green is the new additions, while red is the removals. You can even add the comments on the code changes.
Merge the pull request. Then delete the branch if that not required anymore. This only delete the remote branch, you have to manually delete the local branch. Go to Github Desktop and delete the Styling-branch manually.
```

- Now We add 2 more branches, and do different changes to the style.css file from those 2 branches which will create a conflict.
- Lets see how to merge in that case.
- make 2 branches in remote repo (css-branch1, css-branch2). From Github Desktop, fetch the origin.
- Then checkout css-branch1, then add a simple css rule to H1 tag from style.css file.
- Then commit it. Then Push origin
- Then checkout css-branch2, then add a different css rule to H1 tag from style.css file. Then commit it. Then Push origin

- Go to Github, you can see both the changes as pull requests. Create the pull request from css-branch1. You can automatically merge the pull request since there are no conflicts.

- Then go to the repo, pull request, create new pull request, base: main, compare: css-branch2. We cannot automatically merge since there is a conflict. Anyway we create the pull request and manually mearge. We need to resolve the merge conflict.

```bash
h1 {
<<<<<<< css-branch2
  color: blue;
=======
  background-color: red;
>>>>>>> main
```

- GitHub would says;

  <<< css-branch2 has that code, >>> main branch has this code, so github cannot understand which code is correct. So we need to help him to resolve. Anyway, after resolve, <<<,>>>, and === lines has to be removed. You can keep the top part, or bottom part or you can keep both. Here both are correct so we keep both by deleting above lines. Final code should be like below. Then mark as resolved. Before confirm the merge, check the file changes tab.

```bash
h1 {
  color: blue;
  background-color: red;
}
```

- Now delete both the branches, no longer need them. Fetch and pull from Github Desktop. Suppose you find some error in the final code, go to history tab, right click the commit you need, Revert changes in commit. Then you may need to manually edit a conflict. Do as per the last time and commit the revert.

