# Lab Report 4

## Markdown Parse Repositories
- my markdown-parse repository: [repo](https://github.com/eNebulas/markdown-parse)
- the one I reviewed: [repo](https://github.com/mBookUCSD/markdown-parse)

## Snippet 1
```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```
- Expected output: ``[`google.com, google.com, ucsd.edu]``

## Snippet 2
```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```
- Expected output: `[a.com, a.com(()), example.com]`

## Snippet 3
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
