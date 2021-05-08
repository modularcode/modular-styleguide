# ModularStyleguide

> An opinonated guide about how to organize your app code in modular way


## Naming conventions

#### Use **PascalCase** for the component filenames and their directories, use **camelCase** for the rest of the files.

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

#### Use file extensions that make more sense (assuming SomeComponent contains **JSX** markup)

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

#### Name the test files with `.test.{extension}` or `.spec.{extension}`

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

#### Underscore the aggregational non-component directories

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
