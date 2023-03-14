# Lab Report 5

# A review of lab report 4, and how it could have been made faster using a bash script

Lab report 4 was about speed commands, where we were supposed to complete a certain number of sequential tasks as fast as possible by using the command hisotry 
to access previously used commands.

However, despite being against the rules, a bash script could have done it all *very* quickly. Given all the commands we used were just bash commands with 
java, they could all easily be put into a script.

the first couple of commands that would go into a bash script are quite simple, and are as follows:


```
ssh cse15lwi23xxx@ieng6.ucsd.edu
git clone git@github.com:ucsd-cse15l-w23/lab7.git
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```

However we run into a problem, we want to ideally use nano to edit the file thats incorrect so the tests run properly, but how do we do keyboard inputs using bash?
[This](https://askubuntu.com/questions/20414/find-and-replace-text-within-a-file-using-commands) askUbuntu forum shows a very ugly sed command that is almost enough
to accomplish this task. The only problem is I dont know what to replace the "g" in `sed -i "" 's/index1/index2/g' ListExamples.txt` with to make it replace last occurance
instead of globally. But if I could, this would be the answer to this part.

Finally we would run the java command again and commit

```
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
git add ListExamples.java
git commit -m "fixed"
```

With this, and a proper sed command (since I don't know how to fix the command to make it work), you would have a complete bash script to automate the speed challenge 
faster than any human could. Also since I can't find a proper sed command I can't actually run and test the script irl but theoretically this would work.




