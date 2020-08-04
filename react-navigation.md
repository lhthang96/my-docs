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

  - Render

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
