# How to truncate string with ellipsis

To truncate strings with ellipsis you can do the following:
```css
.truncate {
    overflow: hidden;
    text-overflow: ellipsis;
    width: 100px;
    white-space: nowrap;
}
```
__Notes__:
- A width must be specified
- Please check the `display` property. It might be the case that the value for that property isn't compatible with the ellipsis. Rule of thumbs is to use `inline-block` or `block`. 