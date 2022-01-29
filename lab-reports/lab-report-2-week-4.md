# Lab Report 2

## First Code Error: Infinite Loop
- The first thing we noticed is that the original code entered an infinite loop if you add text after the last link. Here is an example of this:

[test-file2.md](https://github.com/eNebulas/markdown-parse/blob/main/test-file2.md)
```
# Title

[a link!](https://something.com)
[another link!](some-page.html)

some paragraph text after the links
```
- This is the error message that occurred when running with this test case:
![infinite-loop](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/error-1-infinite-loop.png?raw=true)
- We theorized that the reason this occurred is due to the nature of how the `indexOf` method works. We update `currentIndex = closeParen + 1`, but what if `indexOf` returns `-1`, i.e. there are no more close parentheses? Then, `currentIndex = -1 + 1 = 0`, and the loop is now infinite. So, to fix this, we can just add a conditional checking if `closeParen == -1`, then we are done. We also thought that we can just do this for all the variables as if any of them are missing, we do not have a link. That led to the following change:
![first-code-change](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/first-code-change1.png?raw=true)
