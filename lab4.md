# Lab Report 4 - Vim (Week 7) 

## Step 4

![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/668779be-5e54-4182-88aa-a8315c9de72e)

Keys pressed: `<up><enter>` 
* `ssh l2weng@ieng6.ucsd.edu` was the only command in my command history, so pressing the up arrow key accessed it in one press. Running the command is what logs me into ieng6.

## Step 5

![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/a93b7f5d-9884-4f21-9815-e4d1f8f095e5)

Keys pressed: `git<Space>clone<Space>` `<Ctrl + C><Ctrl + V><enter>` 
* I had the forked repository in my clipboard, so after I typed `git clone `, I just pasted the repository to be cloned into the command line and ran it. This cloned the repository onto my ieng6 machine.

## Step 6

![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/41ab462b-c246-44e4-a2e4-1f6630a413a2)

Keys pressed: `cd<Space>lab7` `<enter>` `bash<Space>test.sh` `<enter>` 
* After cloning, my working directory is not in the cloned repository, so typing `cd lab7` and running it, I can now access and run the test file. The test file is a shell script, so I ran it by typing `bash test.sh` as `test.sh` is the file name and entering it. 

## Step 7

![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/89ee859d-495a-4a97-822f-b539d4b11eb0)
![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/742b9b1f-e883-4464-b5e9-f439f03242cd)

Keys pressed: `vim<Space>L` `<Tab>` `.java` `<enter>` 
* This part of the step put me into the Vim text editor of the file that I had to fix. The `<Tab>` filled out the rest of the file name after typing `L`, which was `ListExamples.java`, and I manually typed the rest of the file name. 

Keys pressed: `/index1` `<enter>` `nnnnnnnnner2` `<Esc>` `:wq` `<enter>` 
* The first command searched the file for all occurences of `index1` which was the string to be fixed in the test file. Running and pressing `<enter>` let me search through it, and pressing `n` nine times navigated me to the occurence of `index1` for me to fix. Pressing `e` took me to the last character of the word, and typing `r` and then `2` replaced the last character with `2`, effectively turning the `index1` occurence into `index2`. At this point, I was still in insert mode, so pressing `<Esc>` took me into normal mode, where I saved and quitted the file through the colon command `:wq` and ran it with `<enter>`.

## Step 8

![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/77625ff8-5053-4144-b91b-a40ef7ceb0d1)

Keys pressed:  `bash<Space>test.sh` `<enter>` 
* This command just ran the `test.sh` file to prove that the tests worked after the fix.

## Step 9

![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/409749c3-81f0-46ab-b4d2-1fda8413d696)

Keys pressed: `git<Space>add<Space>L` `<Tab>` `.java` `<enter>`
* This command types `git add` and autocompletes the fill to be prepped to be committed, which is `ListExamples.java`, similar to how the file was autocompleted in the command line for Step 7. After adding the file that was changed, the file is now ready to be committed.

Keys pressed: `git<Space>commit<Space>-m<Space>` `<Shift + '>` `Fixed<Space>tests` `<Shift + '>` `<enter>`
* This command types `git commit` and with the `-m` tag, I filled out my own commit message using quotation marks for the syntax, `Fixed tests`. This commits(saves) my change to the local repository on the ieng6 machine.

Keys pressed: `git<Space>push<Space>origin<Space>main` `<enter>` 
* This command types `git push origin main`, which pushes my changed repository on the branch `main` to the `origin`, which is the remote repository on GitHub.
