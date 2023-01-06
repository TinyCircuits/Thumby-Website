# Submitting a Game to the Thumby Arcade

This tutorial will show you how to add a game to the Thumby Arcade in the <a href="https://code.thumby.us/" target="_blank" alt="TinyCircuits Thumby Editor">**Thumby Code Editor**</a> using <a href="https://github.com/ " target="_blank" alt="Github main website link">**GitHub**</a>!

Consider going through the [**Getting Started with Thumby tutorial**](/Code-Editor/Get-Started/ "Thumby getting started tutorial") before continuing with this one!

---

### Tools needed

*   **Your Thumby game**
*   A <a href="https://github.com/ " target="_blank" alt="Github main website link">**GitHub**</a> account
*   <a href="https://code.thumby.us/" target="_blank" alt="TinyCircuits Thumby Editor">**Thumby Code Editor**</a> - *NOTE: Only Google Chrome and Microsoft Edge support running the TinyCircuits Thumby Code Editor webpage*

---

## Create & Login to GitHub Account

Go to <a href="https://github.com/ " target="_blank" alt="Github main website link">**GitHub.com**</a> and login or create an account. GitHub is a code hosting platform created to track versions of code and collaborate with others.

![GitHub landing page for sign in and sign up](https://cdn.shopify.com/s/files/1/1125/2198/files/github-landing-page-screenshot.jpg?v=1642026563)

Once you have an account, <a href="https://docs.github.com/en/get-started/quickstart/hello-world" target="_blank" alt="GitHub documentation for getting started">**get familiar with GitHub features**</a> like creating a code repository, branching, pushing changes to GitHub from your local machine, and making commits and pull requests to public repositories. You can do all of this through GitHub's website, or you can learn how to do it all from the <a href="https://docs.github.com/en/get-started/using-github/github-cli" target="_blank" alt="GitHub CLI docs">**command line**</a>.

At TinyCircuits, we share all of our software and hardware files through GitHub publicly under the <a href="http://creativecommons.org/licenses/by-sa/3.0" target="_blank" alt="Open Source license details">**Creative Commons Attribution Share-Alike 3.0 License**</a>. Open source contributions lead to greater and faster innovation through sharing and collaboration - you sharing your game on GitHub makes you a part of the amazing open source community!

If you are not quite ready to submit your game and want some feedback, or players to test the game, consider sharing it on the Thumby board of the <a href="http://forum.tinycircuits.com/index.php" target="_blank" alt="TinyCircuits Arduino forum">**TinyCircuits forum**</a> or with the community on our <a href="https://discord.gg/vzf3wQXVvm" target="_blank" alt="Link to join the tinycircuits Discord">**Discord**</a>.

---

## Create Game & Share

Once your game is in a state where you are ready to share it with everyone and publish it to the public Thumby Arcade, <a href="https://github.com/TinyCircuits/TinyCircuits-Thumby-Games/blob/master/README.md" target="_blank" alt="Thumby Game Submission Instructions">**go through the instructions in the README file available on the repository of the Thumby Games**</a> to learn how to name your files, which files to include, and other important details. In short, you will need to submit a folder with 3 (or more) files:


* *GameName/GameName.py* - The main file of your game that references any other files, like a .bin or .raw image you use in the game - include all files needed for your main game file to work!
* *GameName/arcade_description.txt* - Include the title of your game, a short description, your name, and the version of your game. Add any instructions important to play your game. This text is displayed when hovering over your game in the Thumby Arcade.
* *GameName/arcade_title_video.webm* - A .webm video of gameplay. Use the video camera 🎥 button in the Emulator panel of the Thumby Code Editor Website to record a .webm of gameplay. Zoom in to at least 8× to provide a good quality video. The zoom factor displays in the bottom left of the Emulator.

---

## Submit Your Game

The following instructions (with pictures!) will guide you through submitting your game to the Thumby Arcade step-by-step all through your web browser - no need to use the command line if you're not comfortable with it. You just need a GitHub account! 

### Fork Repository

Log in to your GitHub account and navigate to the <a href="https://github.com/TinyCircuits/TinyCircuits-Thumby-Games" target="_blank" alt="Thumby Game Repo & Submission Instructions">**Thumby Games Repository**</a> page. Press the 'Fork' button in the top right of the page to fork your own copy of the repository:


<center>
![Submit Game - fork](/images/submit-game-fork.jpg)
</center>
<center>
*Fork? That's a weird name - [**what does forking a repository mean**](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks)*?
</center>

---

### Add Files to Your Local, Forked Repository

The game files you put together in a folder of the same main game .py file are what you will want to add here. Make sure the folder name and the .py file have the exact same name - this name is case sensitive!

Click the 'Add file' button to access the drop down for the 'Upload files' option.

<center>
![Submit Game - add files](/images/submit-game-add-files.jpg)
</center>
<center>
*Zoomed in look at the buttons*
</center>

<center>
![Submit Game - drag files](/images/submit-game-drag-files.jpg)
</center>
<center>
*The page that appears after selecting 'Upload files'*
</center>

Drag and drop your [GameName] folder to the above window where directed.

#### Commit Game Files

Now that you have added the folder of all the files needed to play your game, you will need to 'Commit' them to finalize your selections. Consider adding a description for these changes, such as "Add a game called [GameName]". Once you're happy with the description, press the 'Commit changes' button:

<center>
![Submit Game - commit files](/images/submit-game-commit.jpg)
</center>
<center>
*Notice the file path says Brickd/Brickd.py - this is how you will want to see your files added, in the right folder!*
</center>

---

### Submit Pull Request

Go back to the main Thumby Games repository and click on the **'Pull Requests'** tab. On this page, press the 'New pull request' button:

<center>
![Submit Game - pull request](/images/submit-game-new-pull-request.jpg)
</center>

Select your local, forked repository to compare changes. Once selected, check that you can see all the files you want to submit. If everything looks good, press the 'Create pull request' button:

<center>
![Submit Game - commit files](/images/submit-game-compare-changes.jpg)
</center>

On the next page, you get the chance to add more information on what exactly is in your pull request. Add some description on the status of your game, and then press the 'Create pull request' button:

<center>
![Submit Game - commit files](/images/submit-game-create-pr.jpg)
</center>

That's all! You should see a successful message that your branch has no conflicts with the base branch. 

<center>
![Submit Game - commit files](/images/submit-game-pr-final.jpg)
</center>

Now that you have submitted a successful pull request, you just need to wait on the TinyCircuits team to accept your game before it's added to the Thumby Arcade. If there are any issues with the PR, a TinyCircuits team member will comment and let you know!

---
