# Lab Report 3

For researching commands, I'll be doing grep. grep has a lot of options, even some really useful ones I'll be exploring in this lab report.
For finding out which command does what, I used a combination of the `--help` command (man grep does not work) and [This Website](https://www.geeksforgeeks.org/grep-command-in-unixlinux/).

First we have `grep -r` (short for recursive) which essentially replaces the job of xargs for grep. 

**Output of each exmaple has been shortened to "..." to prevent them from taking way too much space**
```
grep -r zebra
written_2/non-fiction/OUP/Berk/ch2.txt:Just learned to cut...
written_2/travel_guides/berlitz1/WhereToDublin.txt:        zebra crossings...
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt:        Africa” exhibit, where herds...
written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt:Some inhabitants get a bird’s eye view...
written_2/travel_guides/berlitz2/California-WhereToGo.txt:You approach Hearst Castle...
written_2/travel_guides/berlitz2/California-WhereToGo.txt:The highlight of the park is the San Diego Zoo...
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:Diving is virtually always safe...
```
```
grep -r Lucayans
written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus...
written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered...
```

If I pipe a wall of text directories to grep from the `find` command, instead of searching each directory it will search the entire wall of text that `find` gives it as if 
it was a text file which is normally not what we want. `xargs` solves this by feeding each line as a command to grep, but the 
`-r` also fufills this exact purpose by recursively feeding each line as input. It also means I don't have to use 'grep .txt' to prevent grep from outputting "is a directory," as well as the `find` command to feed grep a list of directories.

Next we have the `grep -c` command. I'm going back to using my double pipe method `find written_2/ | grep .txt | xargs grep` because if I try using `-c` with `-r` it searches a lot of additional stuff that we really don't need to search through (like a lot of .git/objects directories)
and using the double pipe in this situation avoids that.

**The output has been shortened**
```
find written_2/ | grep .txt | xargs grep -c zebra
written_2/non-fiction/OUP/Abernathy/ch1.txt:0
written_2/non-fiction/OUP/Abernathy/ch14.txt:0
written_2/non-fiction/OUP/Abernathy/ch15.txt:0
written_2/non-fiction/OUP/Abernathy/ch2.txt:0
written_2/non-fiction/OUP/Abernathy/ch3.txt:0
written_2/non-fiction/OUP/Abernathy/ch6.txt:0
written_2/non-fiction/OUP/Abernathy/ch7.txt:0
written_2/non-fiction/OUP/Abernathy/ch8.txt:0
written_2/non-fiction/OUP/Abernathy/ch9.txt:0
written_2/non-fiction/OUP/Berk/ch1.txt:0
written_2/non-fiction/OUP/Berk/ch2.txt:1
written_2/non-fiction/OUP/Berk/CH4.txt:0
written_2/non-fiction/OUP/Berk/ch7.txt:0
...
```
```
find written_2/ | grep .txt | xargs grep -c red
written_2/non-fiction/OUP/Abernathy/ch1.txt:24
written_2/non-fiction/OUP/Abernathy/ch14.txt:24
written_2/non-fiction/OUP/Abernathy/ch15.txt:17
written_2/non-fiction/OUP/Abernathy/ch2.txt:32
written_2/non-fiction/OUP/Abernathy/ch3.txt:27
written_2/non-fiction/OUP/Abernathy/ch6.txt:27
written_2/non-fiction/OUP/Abernathy/ch7.txt:26
written_2/non-fiction/OUP/Abernathy/ch8.txt:23
written_2/non-fiction/OUP/Abernathy/ch9.txt:16
written_2/non-fiction/OUP/Berk/ch1.txt:57
...
```

This command, as you might be able to see, prints the amount of times the word occurs in each text file. 
Since the output has been shortened so that this report doesn't end up five more pages than it needs to be, you don't 
get to see the dozen other files that also contain the word, but I promise you they are there.

Another command is the `grep -n` option, which additionally prints out the line number in the txt file where that word appears

**Output has been shortened**
```
grep -r -n zebra
written_2/non-fiction/OUP/Berk/ch2.txt:38:Just learned to cut paper with scissors. If I hold the paper while he cuts and prompt him, he can cut along straight or curved lines. He cut out a square and a circle with help today. I asked him which animals we saw at the zoo, and he mentioned girae and zebra. When I reminded him of the bird and pachyderm houses, he remembered a lot more: the ﬂamingos, parrots, swans, elephants, hippos, and rhinos.
written_2/travel_guides/berlitz1/WhereToDublin.txt:630:        zebra crossings.
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt:1005:        Africa” exhibit, where herds of antelope and zebra graze peacefully in
written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt:54:Some inhabitants get a bird’s eye view of Artis zoo — imagine looking out of your apartment window on a rainy Amsterdam day and seeing a small herd of grazing zebra.
written_2/travel_guides/berlitz2/California-WhereToGo.txt:77:You approach Hearst Castle on a tour bus that climbs the 5 miles (8 km) from the Visitor Center to the hilltop, passing through the parkland that was once Hearst’s private zoo. The lions, monkeys, cheetahs, kangaroos, and polar bears are long gone, but zebra, goats, and Barbary sheep can still 
be seen.
```
```
grep -r -n Lucayans
written_2/travel_guides/berlitz2/Bahamas-History.txt:6:Centuries before the arrival of Columbus...
written_2/travel_guides/berlitz2/Bahamas-History.txt:7:The Spaniards never bothered to settle
```

I suppose if you want to go to the text file itself and find that exact line to read, possibly because the length of the txt provided by grep doesn't have enough information (although there is a command for that too)
then this will tell you exactly where to go one you open the text file. Somewhat useful, but my feeble mind fails to see greater applications that this

And finally, we have the `grep -o` option. 

```
grep -r -o zebra
written_2/non-fiction/OUP/Berk/ch2.txt:zebra
written_2/travel_guides/berlitz1/WhereToDublin.txt:zebra
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt:zebra
written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt:zebra
written_2/travel_guides/berlitz2/California-WhereToGo.txt:zebra
written_2/travel_guides/berlitz2/California-WhereToGo.txt:zebra
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:zebra
```
```
grep -r -o guitar
written_2/non-fiction/OUP/Castro/chB.txt:guitar
written_2/non-fiction/OUP/Castro/chB.txt:guitar
written_2/non-fiction/OUP/Castro/chL.txt:guitar
written_2/non-fiction/OUP/Castro/chL.txt:guitar
written_2/non-fiction/OUP/Castro/chL.txt:guitar
written_2/non-fiction/OUP/Castro/chL.txt:guitar
written_2/non-fiction/OUP/Castro/chM.txt:guitar
written_2/non-fiction/OUP/Castro/chM.txt:guitar
written_2/non-fiction/OUP/Castro/chM.txt:guitar
written_2/non-fiction/OUP/Castro/chM.txt:guitar
written_2/travel_guides/berlitz1/WhatToGreek.txt:guitar
written_2/travel_guides/berlitz1/WhatToJamaica.txt:guitar
written_2/travel_guides/berlitz1/WhatToMadeira.txt:guitar
written_2/travel_guides/berlitz1/WhatToMallorca.txt:guitar
written_2/travel_guides/berlitz1/WhereToDublin.txt:guitar
written_2/travel_guides/berlitz2/China-WhatToDo.txt:guitar
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:guitar
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:guitar
written_2/travel_guides/berlitz2/Crete-WhatToDo.txt:guitar
written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt:guitar
written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt:guitar
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt:guitar
```

If you're like me and you get overwhelmed by the additional text grep provides when searching a term, and you really just want to know
what files have each word without having to use your eyes to sift through the walls of text, `-o` only prints the matching word, dramatically shortening each line.
You mnight have noticed that I didn't have the "this output has been shortened disclaimer" above the code this time, and thats because with `-o` there was so much removed text that
I actually *could* fit the entire thing into a managable code block. Easily my favorite option.



