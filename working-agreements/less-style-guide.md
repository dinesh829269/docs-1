## LESS Style Guide

What is [LESS](http://lesscss.org/)?

> Less is a CSS pre-processor, meaning that it extends the CSS language,
> adding features that allow variables, mixins, functions and many other
> techniques that allow you to make CSS that is more maintainable,
> themeable and extendable.

We don't have a linter to enforce LESS style, however there are some rules
to generally follow:

#### Use classes for styling

```html
<div class="course-title" id="course-title-11">Intro to Computer Science</div>
```

```less
.course-title {
  padding: 10px;
  font-size: 2pt;
}
```

#### Class names should be lowercase hyphenated where necessary

Good:

```html
<span class="course-title"></span>
```

Bad:

```html
<span class="CourseTitle"></span>
```

#### Two space indents

```less
.course-title {
  font-size: 2pt;
  .course-code {
    font-size: 0.5pt;
    color: #999;
  }
}
```

#### Use multiple lines for a rule.

The only exception is if there is only one property in the rule.

Good:

```less
.course-title {
  padding: 10px;
  font-size: 2pt;
}
```

Good:

```less
.course-code { font-size: 0.5pt }
```
