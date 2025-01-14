because of [[The problem with && operator]] it can be an idea to use the more verbose:
`showRender ? render : null`
option instead

In this case, this:
`{showMyData && <p>{mydata}</p>}`

becomes this:
`{showMyData ? <p>{mydata}</p> : null}`

Why do this?
If showMyData is falsy, it is **returned** by the && option. 
This can cause bugs, such as if showMyData was accidentally zero instead of false.

The ternary avoids this and is more readable.