# Remote Access to ieng6 Tutorial


First you'll need vs code, so go to [their website](https://code.visualstudio.com/) and download it to your computer if you don't already have it.
Simply select the operating system your computer runs on and run the executable installer once it finishes downloading
![image](https://user-images.githubusercontent.com/70412955/212784858-258c66f8-ef24-4d65-bf5d-abc52d4b034b.png)

Next you'll need Git Bash, so go here and download that [here](https://gitforwindows.org/).
It might be helpful to set Vscode to git's default editor rather than Vim, unless you are confident in your ability to use Vim.

You now need to get a vscode git bash terminal set up.
1. Open vscode
2. Hit crtl + `
3. Now hit crtl + shift + p
4. In the search bar type 'Select Default Profile'
5. Select Git Bash
6. Click on the drop down menu next to the '+' and select Bash 

![image](https://user-images.githubusercontent.com/70412955/212785709-0701cc2b-3b0b-4838-9836-6591b876e590.png)

8. click the '+' to create a new Git Bash terminal

Next you'll need to look up your particular ieng6 account. To do that, use this other [Guide](https://docs.google.com/document/d/1hs7CyQeh-MdUfM9uv99i8tqfneos6Y8bDU0uhn1wqho/edit)

Take note of the student id you saw when finding the ieng6 account, it should look kind of like this "cs15lwi23zz" with the "zz" being something else $ s

In your bash terminal tpye in `$ ssh cs15lwi23zz@ieng6.ucsd.edu` (with the zz replaced with your specific two letters)

You might get a message about authenticity, simply repsond with yes if its your first time connecting. 

Next it should ask you for a password. If you reset your password in one of the previous guides, enter the password. You won't be able to see what you're typing so be careful

If done correctly you should see this:

![image](https://user-images.githubusercontent.com/70412955/212787053-a55318b3-b963-43ce-9eda-33d5a313864b.png)


Next You can try out some commands! Here's a list of some of them:

`cd ~`

`cd`

`ls -lat`

`ls -a`

Here's what my pc gave for `ls -a`

![image](https://user-images.githubusercontent.com/70412955/212787213-bf803cd6-e61d-4e1a-abb2-3d3c5eece157.png)
