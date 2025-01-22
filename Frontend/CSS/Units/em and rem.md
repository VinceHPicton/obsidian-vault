em and rem are units that are relative to a font size...

**The problem they solve**
- Browsers have a default font-size of 16px. But this can be changed by users such as for accessibility reasons.
- Therefore you should never set font-size to a px value, as it will override the default user-set font-size.
- Using em/rem allow you to scale your sizes according to the user-defined personal font-size set at the browser element.

**em**
em is a unit relative to the font size of the element it is assigned to.

A 2em value corresponds to 2x the font size, so if the font-size it's using was 16px then 2em = 32px.

**You should never use em for font-size**
This is because if em is assigned to the font-size property** (ie like used for `font-size: 1em` as opposed to any other property), it'll be relative to the font size of the parent. If the parent doesn't have one it'll ask it's parent and so on until it hits the root element which if unset ultimately asks for the user-adjustable browser's default font-size.

The problem this can cause it you can get a cascading effect of checking parents, where, like below, the `<li>` font-size in px == the default x 1.5 x 2 x 1 x 2
```
body {
  font-size: 1.5em;
}
.container {
  font-size: 2em;
}
ul {
  font-size: 1em;
}
li {
  font-size: 2em;
}
```

**em is a great unit for padding, margin, border**
This is because it sizes according to the font-size of it's own element, meaning the padding/margin etc will always scale nicely with the font-size of the element without you having to do anything.
```
button {
  font-size: 2rem;
  padding: 1em;
}
```

**rem**
(root em)
This is just like em except it ignores any parents, and **always sizes relative to the root element font-size.**
Therefore it is the correct unit for font-size.