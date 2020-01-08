# HTML: Input type 'number'

Input type number is a nice way in HTML5 for having number input. The following issues will be helpful for using this:

## Protecting from entering negative integers

The `<input type="number">` has a very good feature `min="0"` to protecting against negative integers. But this only works with the step buttons (visible on the right side of the field), and if user enters negative integer by hand, it doesn't validate that. To solve the issue the following `onkeyup` event is well enough minimal solution we found over the internet.

```html
<input type="number" autocomplete="off" min="0" onkeyup="this.value=this.value.replace(/[^0-9]/g,'');">
```

## Currency input

For entering currency (money amount) that means, float values, we found the `<input type="number">` is not a good fit. So we went with the `<input type="text">` with some other validation API for this. With the following example we can accept any amount like: `54645546.12345` (integers with five float values).

```html
<input type="text" autocomplete="off" inputmode="numeric" pattern="[0-9]+(\.[0-9]{0,5})?%?" placeholder="In numbers, eg. 54645546.12345">
```