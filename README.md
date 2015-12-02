# CSS style guide

## Introduction

The CSS style guide in use at Procurios is based on the work of various sources in the past few years. Most of it is based on our own experience with maintaining a large codebase. An important source of inspiration is Harry Roberts, who published his work on [cssguidelin.es](http://cssguidelin.es/). Another inspiring source is [Code Guide, by @mdo](http://codeguide.co/).

## Rules (anatomy and syntax)

A CSS rule is built out of the following blocks:

```css
[selector] {
	[property]: [value];
}
```

The combination of a `property` and a `value` is called a `declaration`.
A typical CSS rule based on this style guide looks as following:

```css
.FooComponent {
	display: block;
	text-align: center;
	color: #fff;
}
```

### Place related selectors on the same line

... and respect the maximum line length.

```css
/** bad */
.FooComponent,
.FooComponent--collapsed {
	display: block;
}

.FooComponent, .FooComponent--collapsed, .BarComponent {
	display: block;
}

.FooComponent, .FooComponent--collapsed, .FooComponent--collapsing, .FooComponent--collapsed {
	display: block;
}

/** good */
.FooComponent, .FooComponent--collapsed {
	display: block;
}

.FooComponent, .FooComponent--collapsed,
.BarComponent {
	display: block;
}

.FooComponent, .FooComponent--collapsed, .FooComponent--collapsing,
.FooComponent--collapsed {
	display: block;
}
```

### Place a property-value pair on the same line

```css
/** bad */
.FooComponent {
	display:
		block;
}

/** good */
.FooComponent {
	display: block;
}
```

### Place each declaration on its own (new) line

```css
/** bad */
.FooComponent {
	display: block; float: left;
}

/** good */
.FooComponent {
	display: block;
	float: left;
}
```

### End each declaration with a semicolon

```css
/** bad */
.FooComponent {
	display: block;
	float: left
}

/** good */
.FooComponent {
	display: block;
	float: left;
}
```

### Declaration order: positioning > box model > typographic > visual

Related property declarations should be grouped together following the order:

1. Positioning
2. Box model
3. Typographic
4. Visual

Positioning comes first because it can remove an element from the normal flow of the document and override box model related styles. The box model comes next as it dictates a component's dimensions and placement.

Everything else takes place inside the component or without impacting the previous two sections, and thus they come last.

For example:

```css
.declarationOrder {
	position: absolute;
	top: 100px;
	left: 100px;
	width: 1000px;
	height: 1000px;
	font: normal 13px "Helvetica Neue", sans-serif;
	color: #444;
	border: 1px solid #e5e5e5;
	background: #f5f5f5;
}
```

## Whitespace

### Use tabs to indent declarations

```css
/** bad */
.FooComponent {
∙∙∙∙display: block;
}

.FooComponent {
∙∙display: block;
}

/** good */
.FooComponent {
	display: block;
}
```

### Place a space before the opening brace

```css
/** bad */
.FooComponent{
	display: block;
}

/** good */
.FooComponent {
	display: block;
}
```

### Place the closing bracket on its own (new) line

```css
/** bad */
.FooComponent {	display: block; }

.FooComponent {
	display: block; }

/** good */
.FooComponent {
	display: block;
}
```

### Place a space after the property-value delimiting colon

```css
/** bad */
.FooComponent {
	display:block;
}

/** good */
.FooComponent {
	display: block;
}
```

### Place the first declaration on a new line after the opening brace

```css
/** bad */
.FooComponent {	display: block;
	color: #fff;
}

/** good */
.FooComponent {
	display: block;
	color: #fff;
}
```

### Limit line length to 80 characters

Where possible, limit the length of a line to a maximum of 80 characters.

```css
/**
 * This comment explains the following CSS in detail. A little bit too many details,
 * because the length of one line exceeds 120 characters. Hence, it's carefully
 * broken into pieces to enhance readability.
 */
```

There will be unavoidable exceptions to this rule (fe. URLs, gradient syntax).

## Indenting

### Don't indent related rules / rulesets

Our naming convention should be sufficient to visualize relations between rules.

```css
/** bad */
.FooComponent {
	...
}

	.FooComponent__bar {
		...
	}

		.FooComponent__baz {

		}

/** good */
.FooComponent {
	...
}

.FooComponent__bar {
	...
}

.FooComponent__baz {

}
```

## Comments

### Don't describe the obvious

We use comments in our CSS files for two purposes:

- Clarification of the document structure.
- Explanation of a specific declaration or rule.

There is no such thing as too much commenting -- as long as a comment improves the maintainability or interchangeability.

### Use sectioning comments if 1 CSS file contains multiple sections

```css
/**
 * This is a sectioning comment and it explains the following CSS in detail.
 */
```

Please note that multiple sections in 1 file might be a code smell. Consider splitting discrete chunks of code into their own files.

### Use inline comments to explain a specific rule or declaration

```css
/** This rule needs some explanation */
.FooComponent {
	overflow: hidden;
}

.FooComponent {
	overflow: hidden; /** This declaration needs some explanation */
}
```

## Naming conventions

We use a BEM-like naming convention. BEM, meaning _Block_, _Element_, _Modifier_, is a front-end methodology coined by developers working at Yandex. Whilst BEM is a complete methodology, here we are only concerned with its naming convention. Further, the naming convention here only is BEM-like; the principles are exactly the same, but the actual syntax differs slightly and is adopted [from Harry Roberts guidelines](http://cssguidelin.es/#bem-like-naming).

BEM splits classes into three groups:

- Block: The sole root of the component.
- Element: A component part of the Block.
- Modifier: A variant or extension of the Block.

To take an analogy:

```css
.person {
	...
}

.person__head {
	...
}

.person--tall {
	...
}
```

### Use camelCase when naming class groups

```css
/** bad */
.sub-content {
	...
}

.subContent__call-to-action {
	...
}

/** good */
.subContent {
	...
}

.subContent__callToAction {
	...
}
```

### Use PascalCase when naming the `Block` of a Component

At Procurios isolated web components are conveniently named Component. Mind the capital `C`. If the CSS belongs to a Component, use the name of the Component as block name.

```css
/** bad */
.filterPanel {
	...
}

.filterPanel__innerContainer {

}

/** good */
.FilterPanel {
	...
}

.FilterPanel__innerContainer {
	...
}
```

### Delimit elements with two underscores

```css
/** bad */
.FooComponent-footer {
	...
}

.fooComponentFooter {
	...
}

/** good */
.FooComponent__footer {
	...
}
```

### Delimit modifiers with two hyphens

```css
/** bad */
.FooComponent-collapsed {
	...
}

.collapsedFooComponent {
	...
}

/** good */
.FooComponent--collapsed {
	...
}
```

## Selectors

I quote [Harry Roberts](http://cssguidelin.es/#css-selectors):

> Poor Selector Intent is one of the biggest reasons for headaches on CSS projects. Writing rules that are far too greedy—and that apply very specific treatments via very far reaching selectors—causes unexpected side effects and leads to very tangled stylesheets, with selectors overstepping their intentions and impacting and interfering with otherwise unrelated rulesets.
>
> CSS cannot be encapsulated, it is inherently leaky, but we can mitigate some of these effects by not writing such globally-operating selectors: **your selectors should be as explicit and well reasoned as your reason for wanting to select something**.

### Use unambiguous and explicit selectors

```css
/** bad */
header ul {
	...
}

/** good */
.siteNav {
	...
}
```

### Aim to write reusable classes

Reusable classes can be moved, recycled and duplicated across projects. They are location independent and can be reused an infinite amount of times.

```css
/** bad */
.metaData dd {
	font-weight: bold;
}

/** good */
.metaData__label {
	font-weight: bold;
}

/** bad */
input.button {
	background: red;
}

/** good */
.btn {
	background: red;
}
```

### Performance

Performance of CSS selectors is more interesting than it is important with today's browsers. If you want to know more about selector parsing, [start here](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Writing_efficient_CSS).

## Specificity

### Don't use IDs

Not only are IDs inherently non-reusable, they are also vastly more specific than any other selector, and therefore become specificity anomalies.

### Use the least number of selectors required to style an element

```css
/** bad */
.FooComponent > .FooComponent__title {
	color: hotpink;
}

/** good */
.FooComponent__title {
	color: hotpink;
}
```

### Use `!important` with care

The general rule is that `!important` is always a bad thing, but all rules have exceptions.

Proactive use of !important is when it is used before you’ve encountered any specificity problems; when it is used as a guarantee rather than as a fix. For example:

```css
.one-half {
    width: 50% !important;
}
```

Reactive use of `!important`` is when it is used to combat specificity problems. In these situations, it is preferable that you investigate and refactor any offending rulesets to try and bring specificity down across the board.

## Media queries

Place media queries as close to their relevant rule sets whenever possible. Don't bundle them all in a separate stylesheet or at the end of the document. Doing so only makes it easier for folks to miss them in the future. Here's a typical setup.

```css
.FooComponent {
	...
}

.FooComponent__avatar {
	...
}

@media (min-width: 480px) {
	.FooComponent {
		...
	}

	.FooComponent__avatar {
		...
	}
}
```