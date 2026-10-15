# Containing Blocks

**Name:** ______________

For each positioned element on your site, name its containing block and say why.
Check every answer: select the element in Elements, then type `$0.offsetParent` in the Console.

| Element | `position` | Containing block | Why | `$0.offsetParent` says |
|---|---|---|---|---|
| `.site-header` | sticky | | | |
| `.badge` | absolute | | | |
| `.overlay` | fixed | | | |
| `.modal` | absolute | | | |

## In your own words

What does "removed from normal flow" mean, and what happens to the elements around it?
Use the badge or the modal as your example.

______________________________________________

Note: `$0.offsetParent` returns `null` for a `fixed` element. Its containing block is the viewport, which isn't an element.
