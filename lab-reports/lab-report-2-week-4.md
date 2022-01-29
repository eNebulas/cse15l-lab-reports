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
![first-code-change](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/first-code-change2.png?raw=true)

## Second Code Error: Not a Link?
- The next thing we noticed is that the code picks up some things that it should not. Here is the example:

[test-file5.md](https://github.com/eNebulas/markdown-parse/blob/main/test-file5.md)
```
# title

[stuff]

paragraph

(page.com)
```
- Here is what gets outputted when running this test:
![not-a-link](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/error-2-not-a-link.png?raw=true)
- We theorized that this occurs due to how we add links to our list. A correctly typed link in markdown should have the following: `](`. In other words, the index of the close bracket and the open parenthesis of any link should differ by 1. The following change solves this issue:
![second-code-change](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/second-code-change.png?raw=true)

## Third Code Error?: Runtime
- The last change we talked about is the positioning of where we checked the index. The test case that brought this up is this one:

[test-file7.md](https://github.com/eNebulas/markdown-parse/blob/main/test-file7.md)
```
)[
```
- Here is what gets outputted when running this test:
![runtime](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/error-3-runtime.png?raw=true)
- Granted, this is the correct output, but our code runs through the entire loop even though we know beforehand that there is no close bracket anywhere. So, after using `indexOf` for each variable, we can check right then if we can exit the loop. The following commit shows this change:
![third-code-change](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/third-code-change.png?raw=true)
