# Figma - Web and mobile application prototyping tool

## Mask and background

## Component

Component is a very powerful utility to create a common shape, object or text, which can be reused in the project. The idea is about grouping all elements with some specific usage like menu icon, menu bar, button,... and create a `master component`. Whenever u wanna use that component, just clone from the `master component` and the cloned component is called `child component`.
<br/>
Keep in mind, when u change style of the `master component`, it will be applied to all the children, but if u change style of any specific child, the rest is unchanged.

> Tip: Create a new page to keep all the reusable components.

> Tip: U can use component to quickly create a set of type for icon like filled, outline or half filled (for rating star icon) by grouping all types of icon to a component. Then, when u need a filled icon, u can just hide the outline and half filled part in the component.

## Constraint for responsive

Whenever u choose a shape, u will see a `Constraint` section on the `Design` tray (on the right side). It's a tool to setup how that shape will be aligned when u change the frame dimension. For example, with a burger menu, u usually see it at the top left corner, so u need to set the constraint property to `Left` for the horizontal and `Top` for the vertical, then u can see, it will stay there regardless u change which dimentions.

> Tip: Sometimes, u need to align shapes inside a specific group of elements, then simply just add them to a frame (right click and choose `Frame selection` or hotkey `Ctrl + Alt + G`), and set the constraint up to it.

## Hot key (for Window)

- `Shift`: multiple select, scale with ratio, drag with alignment (vertical or horizontal).
- `Alt`: cloning elements.
- `Alt + Shift`: cloning with alignment.
- `Ctrl + G`: grouping elements.
- `Ctrl + Shilf + G`: ungrouping elements.
- `Space` + `mouse dragging`: moving view on screen.
- `z`: zoom

## Fonts:

Reference: https://www.figma.com/font-types/

- Handwriting fonts: `Pacifico`.
- Serif fonts: `Lora`.
