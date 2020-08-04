# REACT NAVIGATION PERSONAL DOCS

## Setup project

Current project structure is described as a tree below:

```bash
|-- ./constants
|   |-- ./constants/icons.ts
|   |-- ./constants/index.tsx
|   |-- ./constants/rootTabs.ts
|-- ./screens
|   |-- ./screens/Account
|   |-- ./screens/Activity
|   |-- ./screens/Home
|   |-- ./screens/Messages
|   |-- ./screens/Payment
|   |-- /index.ts
|-- ./utils
    |-- ./utils/index.ts
    |-- ./utils/renderIcon.tsx

```

## Notes

### There are 3 types in total to nagivate screens:

- **Stack Navigation**:

  - Save screens history as stack, have a same mechanism with web history.
  - Usually control by screen header.
  - Common use cases: detail or description screen, modal,...

- **Tabs Navigation**:

  - Usually bottom tabs control, which is used as an app menu.
  - Common use cases: app menu, multiple product item such as a laptop product, we will have technical info tab, description tab, ratings and reviews tab,...

- **Drawer**:
  - As its name described, a menu which is stored in a drawer.
  - You can swipe from the edge of the screen, usually on the left side to open the drawer.
  - Common use cases: app menu, user profile info menu,...

### Render behavior

- **Stack Navigation**:
  To illustrate easily, lets take our example, `Home` screen. At `Home` screen, we will switch between 2 stacks, `Home Content` and `Home Modal`. The stack rendering behavior will be described as below:
  - First of all, `Home` screen is rendered.
  - Then we have the initial stack will be rendered right after that, so `Home Content` will be rendered.
  - Next, when we click to open the `Home Modal`, of course the `Home Modal` will be rendered, **however**, `Home Content` has not been unmounted yet. It is stayed in stack, and yeah, for the `goBack` method, specified by stack navigator, so the componentWillUnmount of `Home Content` is not called.
  - Finally, when we go back to `Home Content`, the componentWillUnmount of `Home Modal` will be called, but componentDidMount of `Home Content` won't be, cause it remains mounted on the stack already.

> **Important**: every time we navigate between tabs, the `Home` screen will trigger its render, it means the componentDidMount of `Home` screen will be called every time we navigate.

- **Tabs Navigation**:
  - We can control tabs rendering behaviour by the "lazy" props, already provided in the library.
  - Default "lazy" is set to true, which means the screen of each tab only render when you navigate to it.
  - Also, the render only occurs once, at the first time u navigate, it will stay there until u reload the apps.

## Tips

### How to create a tree like project structure above

- Go to http://gnuwin32.sourceforge.net/packages/tree.htm
- Download the install file with description "Complete package, except sources"
- Install the setup.exe
- Go to installed tree directory, default is `C:\Program Files (x86)\GnuWin32\bin`, copy `tree.exe`
- Paste it to installed git directory, default is `C:\Program Files\Git\usr\bin`.
- All done, to check if it worked, open git bash and type command `tree`.
