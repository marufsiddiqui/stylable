---
id: guides/shared-classes
title: Shared Classes
layout: docs
---

When building a [Stylable component library](./stylable-component-library.md) or a [Stylable application](./stylable-application.md), it is useful to reuse classes that can be shared across components to achieve common CSS with lower specificity.

## Define a shared class

In your project's [Stylable stylesheet](./project-commons.md), which is used for the commonly used components in your project (named `project.st.css` as recommended), you define a CSS class with a descriptive name like `emphasisBox`.

```css
@namespace "project";
.emphasisBox {
    background: pink;
    color: white;
}
```

## Use shared classes in components

Component **Stylable** stylesheet can use and extend shared classes.

```css
@namespace "comp";
:import {
    -st-from: './project.st.css';
    -st-named: emphasisBox;
}
/*
selector: .comp__root .project__emphasisBox
js value: "project__emphasisBox"
*/
.emphasisBox { }
/*
selector: .comp__root .comp__messageBox.project__emphasisBox
js value: "comp__messageBox project__emphasisBox"
*/
.messageBox {
    -st-extends: emphasisBox;
}
```