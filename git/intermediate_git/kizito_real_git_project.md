### Introduction

This is a page created to practice using git in the real world.

#### Initial setup

1. I started by navigating to [The Odin Curriculum Repository](https://github.com/TheOdinProject/curriculum/tree/main) and forked the original ("upstream") repository into my own GitHub account by using the "fork" button at the top of that repo's page on GitHub.
1. I cloned my forked repository onto my local machine using something like `git clone git@github.com:your_user_name_here/curriculum.git` (you can get the url from the little widget on the sidebar on the right of that repo's page on GitHub).
1. I setup `upstream` by setting it up as another remote since i already have a remote that is pointing to `origin`, which is my folk on GitHub. In order for me to be able to pull directly from the original repository which is `upstream`, i had to set another remote using

```bash
git remote add upstream git@github.com:TheOdinProject/curriculum.git
```

#### Ongoing workflow

1. I started by creating a new feature branch for whatever feature i wanted to build and added this new features.
1. When i finished building this features, odds are that someone has made changes to the upstream repository in the meantime. that means that my `main` branch is probably out of date. I fetched most of the updated copy using `git fetch upstream`.
1. I then merged the changes from the upstream repository into my `main` branch using `git merge`. Specifically, i first made sure i was on my `main` branch by using `git checkout main` to checkout to main andd then `git merge upstream/main` to merge in those upstream changes that i fetched.
1. now that my `main` branch is up-to-date with upstream, i merged it into my featured branch and this because anytime we are merging in more "senior" branches (e.g. mergin the geature into `main`), i want it to be a clean and conflict-free merge if possible. So i first merged the "senior" branch into my dirty branch to resolve conflicts by running `git checkout my_feature_name` to jump back onto my feature branch, then `git merge main` to merge `main` into it.
<div class="lesson-note" markdown="1">

Note that a `git fetch upstream` followed by a `git merge upstream/some_branch` is the Exact same thing as doing a `git pull upstream some_branch`. i prefer to split it up here so that i can explicitly work you throught the steps.

</div>

1. Once i have resolved all conflicts, i can then push my changes to my forked repository

#### Sending my pull request

1. Now that my feature branch is squeaky clean and i know it'll merge cleanly into `main`, the hard part is all over. All that's left is to make the Pull Request (often abbreviated as PR) against our `upstream` repo on GitHub!
1. Now i sent my feature branch back to my `origin` (my fork of the `upstream` repository). you can't send directly to `upstream` because i didn't have access, so i'll need to make a pull request. Use `git push origin my_feature_name` to ship my feature branch up to my fork on GitHub. I **_stopped at this point_**.
1. In a real world project, if i have completed an assigned issue, final point is to submit a pull request to merge my feature branch into he original `upstream` repository's `main` branch. This can be done using Github's interface.
1. Now i can go to my fork on GitHub and click the "Compare & pull request"
1. I can then write a description of what i did and why i did it and then click "Create pull request" and then i can wait for the maintainer to review my PR and merge it in.
