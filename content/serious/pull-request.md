+++
slug = "pull-request"
title = "How to make a GitHub pull request"
date = "2023-12-05"
description = "A step-by-step tutorial on how to make a GitHub pull request, with explanations and commands!"
tags = [
    "github",
    "programming",
    "tutorials",
]
+++

Let's say you want to change someone else's GitHub repository! Maybe you want to fix code, fix typos, or even add new stuff. To do that, unless you already have permission to write to - to change - the repository, you'll have to submit a pull request. The pull request is a request to add your changes to the repository. If the person who maintains the repository approves of your changes, they can approve the pull request and merge its changes with that of their repository.

To make a pull request (a PR, for short), you'll need to follow a series of steps. These are what they are.

For simplicity, I'm going to assume you're using a similar configuration to me (using the GitHub website in conjunction with the terminal for `git`). If you want to do things entirely through the website, or through GitHub's own command-line tool, the steps will be different.

So here's what my steps are!

1. Fork the repository

To make a pull request, the first thing you have to do is to make a fork of the repository. This copies it to your personal profile, where you can make your own changes to submit later. Any changes you make to a fork do not affect the original repository.

2. Clone the forked repository

Clone the repository. This downloads the repository to your computer so you can make changes to its files. You do this using the command:

`git clone LINK_TO_REPOSITORY`

Some repositories can be really big! My first pull request, for example, was submitted to the repository for the Rust programming language. Its repository was 1.13 GB in size! It took several minutes to download and check, and I'm glad my computer had enough space for it in its specific drive.

If you want to clone a large repository and you don't care about all its past history, you can only clone the most recent version of the tree. This is done using the command:

`git clone LINK_TO_REPOSITORY --depth=1`

This fetches only the most recent commit in the repository, which can reduce the size of the data you download. My friend tried to clone their 4 GB `nixpkgs` repository using this method and only needed to download 43.7 MB of data.

3. Make your own branch

Enter the repository's folder and use Git to make your own branch. This branch is where you'll make your changes to submit later. You can make a branch using the commands:

```
git branch BRANCH_NAME
git checkout BRANCH_NAME
```

The first command - `git branch BRANCH_NAME` - creates a new branch in the repository with name `BRANCH_NAME`, and the second command (`git checkout BRANCH_NAME`) moves you to that branch so you can commit your changes to it.

You can also shorten and combine the two of them into a single command:

`git checkout -b BRANCH_NAME`

This both creates the branch and moves you onto it.

As an alternative to `git checkout -b`, you can use

`git switch -c BRANCH_NAME`

This does the same thing, but was introduced to avoid overloading the `git checkout` command. It also serves as a safety guard to prevent you from accidentally misusing the `git checkout` command and causing unintended consequences. This is the recommended option.

Once you're on a new branch, you can start making changes.

4. Make your changes

Now it's time to make the changes you wanted to make! Pull up your text editor and edit some files! Maybe even add some images or documents, if that's what you wanted to do. Even deleting or rearranging things in the repository counts as a change.

5. Commit your changes

Once you've finished making your changes, you need to **commit** them if you want to save them to Git. You can do this using two commands:

```
git add .
git commit
```

The first command - `git add .` - adds all of the changed files in the repository to a list so they can be committed. You can replace the `.` with a list of files separated by spaces, if you want to add individual files. The second command (`git commit`) commits your changes to the repository. This saves them for future use. When you use `git commit`, it should bring up a text editor window inviting you to add a commit message. This is a short message that explains what your commit does. It's typically in an imperative tense. An example of this is:

> Fix typo in README.md

(which was the first commit I made in my first-ever pull request).

It should also show you a list of files that are going to be committed. If you see something on the list that shouldn't be there, or don't see something that should, you can quit your text editor without typing a message (entering a message) to abort the commit.

You can also commit files using a single command:

`git commit -a`

This commits all the files with changes that have already been added to the repository. It's not the same thing as the previous command, through - if you add a new file, you'll have to add it using `git add` before this command can work on it.

6. Push your changes

Now that you've made your changes, it's time to push them! This means (this is) uploading them back to GitHub, so they can be merged in your pull request afterwards. To do this, use the following command:

`git push origin BRANCH_NAME`

and enter your credentials when the password screen asks for them. The repository you're using should typically have an origin. If there is none, or if you want to change it (for example, change it from HTTPS authentication to SSH authentication), you can first remove the old origin with this command:

`git remote rm origin`

`origin` isn't always the name of the origin remote, but it's a very common one. If the repository you're pushing to uses a different name for the origin, you should replace `origin` in the command with that name instead.

Then, you can add a new origin with this command:

`git remote add origin LINK_NAME`

where `LINK_NAME` is the link to the repository.

Once you've added a new origin, you can push your changes to the remote with this command:

`git push -u origin BRANCH_NAME`

where `BRANCH_NAME` is the name of the new branch you're currently on - the one you made back in step 3.

7. Make your pull request

It's finally time to make the pull request you've been working on! This is what you wanted to do in the first place, isn't it? To do this, you'll finally need to leave the terminal and go to GitHub's website. I know, I know - you poor thing, you, having to re-enter the world of GUIs. But fear not! It's really quick and simple.

If you've just pushed your changes recently, when you go to your forked repository's page on GitHub, you'll see a new button above the list of files in your repository. The button will let you make a pull request. Click on the button, enter a title and description for your pull request, and submit it! You're done!!!

If you want to stay in the terminal a little bit longer, look carefully at the result message after you push your changes. There'll be a link to let you make a pull request. The link does the same thing as the button. Click on the link, enter a title and description for your pull request, and submit it! You're done!!!

8. Wait!

Now it's time to wait! The people who maintain the repository you're making a pull request to need to review your pull request and decide if they want it to be in their repository. If they think it's good, they can merge it with their repository. If they think it's bad, they can reject and close it. If they have reservations or comments, they can send you messages about it, so stay alert! You'll want to pay attention to and discuss their suggestions if you want your pull request to be accepted.

If you got it accepted: congratulations!
If you didn't: oh well. You can always try again with something else later.
If you're still waiting on comments: I hope it goes well for you! Hopefully you'll be able to follow their suggestions and make something that works.

### Conclusion

To make a change to someone else's repository, you'll need to make a pull request. This is how you do it:

Fork → clone → branch → change → commit → push → make a pull request → wait!

Keep your attention open and your wits about you, and you'll be able to spot more things you want to fix or change. Keep your mind open and listen to suggestions, and you'll be able to get your fixes and changes accepted by others. Open source software is a community endeavor. I hope you'll be able to contribute to the community and make the world better for other people. Best of luck!
