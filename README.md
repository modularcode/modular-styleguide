# Modular Styleguide

> An opinonated guide about how to organize your app code in modular way


## Naming conventions

### Use **PascalCase** for the component-related filenames and their directories, use **camelCase** for the rest of the files.

```
# Bad

src/
  Main.js
  someComponent/
    someComponent.jsx
```
  
```
# Good

src/
  main.js
  otherNonComponentFile.js
  SomeComponent/
    SomeComponent.jsx

```

There can be an exceptions for this rule though when declaring TypeScript interfaces

```
# bad

src/
  user.ts
```


```
# good

src/
  User.ts
```


```
# even better

src/
  _types/
    User.ts
```

### Use file extensions that make more sense (assuming SomeComponent contains **JSX** markup)

```
# Bad

src/
  SomeComponent/
    SomeComponent.js
```

```
# Good

src/
  SomeComponent/
    SomeComponent.tsx

src/
  SomeComponent/
    SomeComponent.jsx
```

### Name the test files with `.test.{extension}` or `.spec.{extension}`

```
# Bad

src/
  someFile.js
  someFileTest.js
  SomeComponent/
    SomeComponent.jsx
    SomeComponentTest.jsx
```

```
# Good

src/
  someFile.js
  someFile.spec.js
  SomeComponent/
    SomeComponent.jsx
    SomeComponent.spec.jsx
```

### Use `Base`, `The`, `App` naming convention for reusable components

```
# Bad

Button/
Dropdown/
Footer/
Header/
Icon/
Sidebar/
Typography/
```

```
# Good

BaseButton/
BaseDropdown/
BaseIcon/
BaseTypography/
TheFooter/
TheHeader/
TheSidebar/
```


```
# Good

AppFooter/
AppHeader/
AppSidebar/
BaseButton/
BaseDropdown/
BaseIcon/
BaseTypography/
```

### Underscore the aggregational non-component directories

```
# Bad

src/
  config/
  layouts/
  OtherComponent/
  services/
  SomeComponent/
  styles/
```


```
# Good

src/
  _config/
  _layouts/
  _services/
  _styles/
  OtherComponent/
  SomeComponent/
```

In the bad example we need to spend more time figuring out what type of directories are responsible for which things. Also the ordering is messed up, we have organizational directories like `services/` in between two component directories.

In contrast in the good example we can immediately visually distinguish ComponentDirectories from non-component directories. The IDEs will show the directories with underscore on top of the project file explorer which is very convenient.

## Code organization

### Keep components self-contained

```
# Bad

src/
  assets/
    MyComponentRelatedImg.svg
  MyComponent/
    MyComponent.jsx
  styles/
    MyComponent.scss
tests/
  unit/
    MyComponent.spec.jsx
storybook/
  MyComponent.stories.mdx
```


```
# Good

src/
  MyComponent/
    MyComponent.jsx
    MyComponent.scss
    MyComponent.spec.jsx
    MyComponent.stories.mdx
    MyComponentRelatedImg.svg

```

```
# Good

src/
  MyComponent/
    _tests/
      MyComponentMocksData.jsx
      MyComponentMocks.jsx
      MyComponent.spec.jsx  
    MyComponent.jsx
    MyComponent.scss
    MyComponent.stories.mdx
    MyComponentRelatedImg.svg
```

In the bad example the component related files are scattered across the project directories, so when working on that component we will have to jump back and forth through directories which is super inefficient. 

In contrast in the good example all the files related to the component are under the hand, which makes `MyComponent` more maintainable and self-contained.



### Place reusable components into  `_common` or `_components` directory


```
# Bad

src/
  components/
    BaseButton.jsx
    TheHeader.jsx
```


```
# Bad

src/
  components/
    BaseButton/
      BaseButton.jsx
    TheHeader/
      TheHeader.jsx
```


```
# Good

src/
  _components/
    BaseButton/
      BaseButton.jsx
    TheHeader/
      TheHeader.jsx
```

```
# Good

src/
  _common/
    BaseButton/
      BaseButton.jsx
    TheHeader/
      TheHeader.jsx
```


### The hierarchy of components should represent the app hierarchy

```
# Bad

src/
  components/
    Button/
    Title/
    
  pages/
    AuthPage/
    AuthLoginPage/
    AuthSignupPage/
    BlogPage/
    BlogArticlesPage/
    BlogArticlePage/
    BlogArticleEditPage/
    DocsPage/
    TutorialPage/
    TutorialItemPage/
    
  templates/
    Header/
    Sidebar/
    Footer/
    
  utils/
    auth.js
  
```


```
# Good

src/
  _common/
    BaseButton/
    BaseTitle/
    TheHeader/
    TheSidebar/
    TheSidebar/
    
  AuthPage/
    _common/
      AuthHeader/
    _services/
      authService.js
    AuthLoginPage/
    AuthSignupPage/
    
  BlogPage/
    BlogListPage/
    BlogItemPage/
    BlogEditorPage/
    
  DocsPage/
  
  TutorialsPage/
    TutorialsListPage/
    TutorialsItemPage/
```
