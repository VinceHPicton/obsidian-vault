Has 2 possible options, content-box (default) and border-box.

**DEFAULT:** `box-sizing: content-box` 
*Padding and border cause the element to expand*

The `width` and `height` of the element **apply only to the content area**. Padding is added outside the content area, increasing the total size of the element.

- width/height = content
- actual div size = content + padding + border
- Therefore `width` and `height` do not define the actual width and height of elements



**Alternative:** `box-sizing: border-box`
*Padding and border **do not** cause the element to expand*

The `width` and `height` of the element **include the content, [[Padding]], and [[Border]]**. Padding does not increase the total size but instead reduces the content area.

- width/height = content + padding + border
- actual div size = content + padding + border
- Therefore `width` and `height` define the actual width and height of elements

It is best practice to add `box-sizing: border-box` to a [[Global resets]]
