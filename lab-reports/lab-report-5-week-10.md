# Lab Report 5

## How we found these tests
- To find all the differences between our group's implementation and the given implementation in Week 9, we used the `diff` command as outlined in the lab directions. Here's how we did it.

![cloning](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-5/cloning-repos-into-ieng6.png?raw=true)
- First step is to clone both our group's implementation and the given implementation into `ieng6` as a lot of the commands used do not exist natively on Windows, so we use the Linux system remotely using `ieng6`.

![script-change](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-5/changing-bash-script.png?raw=true)
- In order to get the results in a nice format, we edit the given bash script which runs all the test files in `test-files/` to also show the file name.

![results-politz](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-5/results-politz.png?raw=true)
- Now, using the bash script, we can put our results into a file called `results.txt`.

![copy-files](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-5/copy-files-to-my-repo.png?raw=true)
- To do the same with our implementation, we first copy the tests in `test-files/` and the script in `script.sh` into the repository for our implementation.

![results-fireflies](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-5/results-fireflies.png?raw=true)
- Once again, using the bash script, we can put our results into a file called `results.txt`.

![differences](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-5/differences.png?raw=true)
- Using the `diff` command, we can put all the different between the two `results.txt` files into a file called `differences.txt`. From here, we can manually check which implementation is correct for all the files listed in `differences.txt`. After searching for some time, we found the following test cases. The given implementation is correct for `41.md` while our implementation is correct for `201.md`. Let's look into why this is the case.

## Test 1: `41.md`
```
[a](url &quot;tit&quot;)
```
- Due to the appearance of a quote inside the link area, this file has no links. Looking at the differences above, we can see that the given implementation is correct. 
- Our code takes a naive approach when grabbing the links as we are looking for the existence of the characters `[, ], (, )` and if the character sequence `](` exists.

![our-code-snippet](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-5/fix-our-code.png?raw=true)
- A fix for this specific case would be to check for &quot;illegal&quot; characters inside the link area which no longer makes it a link. Things like spaces and quotes would be checked before we add the link to our ArrayList. This could be done by adding some `if` clauses in the snippet above where we add links to `toReturn`.

## Test 2: `201.md`
```
[foo]: <bar>(baz)

[foo]
```
- Due to the appearance of hidden text before the link area, this file has no links. Looking at the differences above, we can see that our implementation is correct.
- It seems that the given implementation does not check the characters between `]` and `(`.

![their-code-snippet](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-5/fix-their-code.png?raw=true)
- A fix for this specific case would be to check for &quot;illegal&quot; characters in between `]` and `(` which no longer makes it a link. Things like `<` and `>` would be checked, but things like spaces or `:` would not before we add the link to our ArrayList. This could be done by adding some `if` clauses in the snippet above where they add links to `toReturn`. This can be implemented using the values of `nextCloseBracket` and `openParen` and a substring for all the characters in between these two indices. From here, they could check for &quot;illegal&quot; characters using `contains`.
