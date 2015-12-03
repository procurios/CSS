# CSS style guide

## Table of Contents

- [Introduction](#introduction)
- [Rules (anatomy and syntax)](#rules-anatomy-and-syntax)
	- [Place related selectors on the same line](#place-related-selectors-on-the-same-line)
	- [Place a property-value pair on the same line](#place-a-property-value-pair-on-the-same-line)
	- [Place each declaration on its own (new) line](#place-each-declaration-on-its-own-new-line)
	- [End each declaration with a semicolon](#end-each-declaration-with-a-semicolon)
	- [Declaration order: positioning > box model > typographic > visual](#declaration-order-positioning--box-model--typographic--visual)
- [Whitespace](#whitespace)
	- [Use tabs to indent declarations](#use-tabs-to-indent-declarations)
	- [Place a space before the opening brace](#place-a-space-before-the-opening-brace)
	- [Place the closing bracket on its own (new) line](#place-the-closing-bracket-on-its-own-new-line)
	- [Place a space after the property-value delimiting colon](#place-a-space-after-the-property-value-delimiting-colon)
	- [Place the first declaration on a new line after the opening brace](#place-the-first-declaration-on-a-new-line-after-the-opening-brace)
	- [Limit line length to 80 characters](#limit-line-length-to-80-characters)
- [Indenting](#indenting)
	- [Don't indent related rules / rulesets](#dont-indent-related-rules--rulesets)
- [Comments](#comments)
	- [Don't describe the obvious](#dont-describe-the-obvious)
	- [Use sectioning comments if 1 CSS file contains multiple sections](#use-sectioning-comments-if-1-css-file-contains-multiple-sections)
	- [Use inline comments to explain a specific rule or declaration](#use-inline-comments-to-explain-a-specific-rule-or-declaration)
- [Naming conventions](#naming-conventions)
	- [Use camelCase when naming class groups](#use-camelcase-when-naming-class-groups)
	- [Use PascalCase when naming the `Block` of a Component](#use-pascalcase-when-naming-the-block-of-a-component)
	- [Delimit elements with two underscores](#delimit-elements-with-two-underscores)
	- [Delimit modifiers with two hyphens](#delimit-modifiers-with-two-hyphens)
- [Selectors](#selectors)
	- [Use unambiguous and explicit selectors](#use-unambiguous-and-explicit-selectors)
	- [Aim to write reusable classes](#aim-to-write-reusable-classes)
	- [Performance](#performance)
- [Specificity](#specificity)
	- [Don't use IDs](#dont-use-ids)
	- [Use the least number of selectors required to style an element](#use-the-least-number-of-selectors-required-to-style-an-element)
	- [Use `!important` with care](#use-important-with-care)
- [Media queries](#media-queries)

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

MDN has [a great piece on CSS syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax) if you want to learn more.

### Place each selector on its own (new) line

```css
/** bad */
.FooComponent, .FooComponent--collapsed {
	display: block;
}

/** good */
.FooComponent,
.FooComponent--collapsed {
	display: block;
}
```

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

### Declaration order: positioning > box model > typographic > visual

Related property declarations should be grouped together following the order:

1. Positioning
2. Box model
3. Typographic
4. Visual

Positioning comes first because it can remove an element from the normal flow of the document and override box model related styles. The box model comes next as it dictates dimensions and placement.

Everything else takes place inside the component or without impacting the previous two sections, and thus they come last.

For example:

```css
.declarationOrder {
	position: absolute;
	top: 100px;
	left: 100px;
	width: 1000px;
	height: 1000px;
	border: 1px solid #e5e5e5;
	font: normal 13px "Helvetica Neue", sans-serif;
	color: #444;
	background: #f5f5f5;
}
```

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

### Limit line length to 80 characters

Where possible, limit the length of a line to a maximum of 80 characters.

```css
/**
 * This comment explains the following CSS in detail. A little bit too many
 * details, because the length of one line exceeds 120 characters. Hence,
 * it's carefully broken into pieces to enhance readability.
 */
```

There will be unavoidable exceptions to this rule (fe. URLs, gradient syntax).

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

## Comments

### Don't describe the obvious

We use comments in our CSS files for two purposes:

- Clarification of the document structure.
- Explanation of a specific declaration or rule.

There is no such thing as too much commenting -- as long as a comment improves the maintainability or interchangeability.

[↑ back to top](#table-of-contents)

### Use sectioning comments if 1 CSS file contains multiple sections

```css
/**
 * This is a sectioning comment and it explains the following CSS in detail.
 */
```

Please note that multiple sections in 1 file might be a code smell. Consider splitting discrete chunks of code into their own files.

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

## Naming conventions

We use a BEM-like naming convention. BEM, meaning _Block_, _Element_, _Modifier_, is a front-end methodology [coined by developers working at Yandex](https://tech.yandex.com/bem/). Whilst BEM is a complete methodology, here we are only concerned with its naming convention. Further, the naming convention here only is BEM-like; the principles are exactly the same, but the actual syntax differs slightly and is adopted [from Harry Roberts guidelines](http://cssguidelin.es/#bem-like-naming).

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

### Performance

Performance of CSS selectors is more interesting than it is important with today's browsers. If you want to know more about selector parsing, [start here](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Writing_efficient_CSS).

[↑ back to top](#table-of-contents)

## Specificity

### Don't use IDs

Not only are IDs inherently non-reusable, they are also vastly more specific than any other selector, and therefore become specificity anomalies.

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)

### Use `!important` with care

The general rule is that `!important` is always a bad thing, but all rules have exceptions.

Proactive use of !important is when it is used before you’ve encountered any specificity problems; when it is used as a guarantee rather than as a fix. For example:

```css
.one-half {
    width: 50% !important;
}
```

Reactive use of `!important`` is when it is used to combat specificity problems. In these situations, it is preferable that you investigate and refactor any offending rulesets to try and bring specificity down across the board.

[↑ back to top](#table-of-contents)

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

[↑ back to top](#table-of-contents)