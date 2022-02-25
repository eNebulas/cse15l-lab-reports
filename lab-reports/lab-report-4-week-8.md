# Lab Report 4

## Markdown Parse Repositories
- my markdown-parse repository: [repo](https://github.com/eNebulas/markdown-parse)
- the one I reviewed: [repo](https://github.com/mBookUCSD/markdown-parse)

## Snippet 1 (Did not pass)
```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```
- Expected output: ``[`google.com, google.com, ucsd.edu]``
- Test:

![Snippet 1](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-4/snippet-1-test.png?raw=true)
- My test result:

![Snippet 1 My Test Result](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-4/running-snippet-1-test-my-repo.png?raw=true)
- Their test result:

![Snippet 1 Their Test Result](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-4/running-snippet-1-test-their-repo.png?raw=true)

## Snippet 2 (Did not pass)
```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```
- Expected output: `[a.com, a.com(()), example.com]`
- Test:

![Snippet 2](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-4/snippet-2-test.png?raw=true)
- My test result:

![Snippet 2 My Test Result](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-4/running-snippet-2-test-my-repo.png?raw=true)
- Their test result:

![Snippet 2 Their Test Result](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-4/running-snippet-2-test-their-repo.png?raw=true)

## Snippet 3 (Did not pass)
```
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
    https://ucsd-cse15l-w22.github.io/
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```
- Expected output: `[https://ucsd-cse15l-w22.github.io/]`
- Test:

![Snippet 3](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-4/snippet-3-test.png?raw=true)
- My test result:

![Snippet 3 My Test Result](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-4/running-snippet-3-test-my-repo.png?raw=true)
- Their test result:

![Snippet 3 Their Test Result](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-4/running-snippet-3-test-their-repo.png?raw=true)

## Questions
- Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.
    - I think that there is a code change to make my program work for snippet 1 and all related cases that use inline code with backticks. It should just be a few if statements and keeping tracks of the indices of the backticks in relation to our four variables for the open and close parentheses and brackets. Granted, this change will be closer to 20-30 lines of code, but it is not going to be too involved.
- Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.
    - I do not think that there is a small code change to make my program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets. Currently, my program takes a naive approach of looking for the existence of the characters `[, ], (, )` and if the character sequence `](` exists. A complete overhaul of how we detect these characters would be necessary to properly deal with all cases that nest these characters.
- Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.
    - I think that there is a small code change that will make my program work for snippet 3 and all related cases that have newlines in brackets and parentheses. It should be a few if statements checking for the existence of new line characters in between any brackets. However, there will likely be some obscure cases that still fail even with this small change due to the naive approach my program takes when it finds links as explained in the previous question.
