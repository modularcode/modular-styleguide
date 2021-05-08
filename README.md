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
