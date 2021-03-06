# CSS style guide

## Table of Contents

- [Introduction](#introduction)
- [Rules (anatomy and syntax)](#rules-anatomy-and-syntax)
	- [Place each selector on its own (new) line](#place-each-selector-on-its-own-new-line)
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
- [Selectors](#selectors)
	- [Use classes to select elements](#use-classes-to-select-elements)
	- [Aim to write reusable classes](#aim-to-write-reusable-classes)
	- [Performance](#performance)
- [Specificity](#specificity)
	- [Don't use IDs](#dont-use-ids)
	- [Use the least number of selectors required to style an element](#use-the-least-number-of-selectors-required-to-style-an-element)
	- [Use `!important` with care](#use-important-with-care)
- [Media queries](#media-queries)
- [Element queries](#element-queries)

## Introduction

The CSS style guide in use at Procurios is based on various sources and experiences in the past few years. Most of it is based on our own experience with maintaining a large codebase. An important source of inspiration is Harry Roberts, who published his work on [cssguidelin.es](http://cssguidelin.es/). Another inspiring source is [Code Guide, by @mdo](http://codeguide.co/).

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
.fooBlock {
	display: block;
	text-align: center;
	color: #fff;
}
```

MDN has [a great piece on CSS syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax) if you want to learn more.

### Place each selector on its own (new) line

```css
/** bad */
.fooBlock, .fooBlock--collapsed {
	display: block;
}

/** good */
.fooBlock,
.fooBlock--collapsed {
	display: block;
}
```

[↑ back to top](#table-of-contents)

### Place a property-value pair on the same line

```css
/** bad */
.fooBlock {
	display:
		block;
}

/** good */
.fooBlock {
	display: block;
}
```

[↑ back to top](#table-of-contents)

### Place each declaration on its own (new) line

```css
/** bad */
.fooBlock {
	display: block; float: left;
}

/** good */
.fooBlock {
	display: block;
	float: left;
}
```

[↑ back to top](#table-of-contents)

### End each declaration with a semicolon

```css
/** bad */
.fooBlock {
	display: block;
	float: left
}

/** good */
.fooBlock {
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
.fooBlock {
∙∙∙∙display: block;
}

.fooBlock {
∙∙display: block;
}

/** good */
.fooBlock {
	display: block;
}
```

[↑ back to top](#table-of-contents)

### Place a space before the opening brace

```css
/** bad */
.fooBlock{
	display: block;
}

/** good */
.fooBlock {
	display: block;
}
```

[↑ back to top](#table-of-contents)

### Place the closing bracket on its own (new) line

```css
/** bad */
.fooBlock {	display: block; }

.fooBlock {
	display: block; }

/** good */
.fooBlock {
	display: block;
}
```

[↑ back to top](#table-of-contents)

### Place a space after the property-value delimiting colon

```css
/** bad */
.fooBlock {
	display:block;
}

/** good */
.fooBlock {
	display: block;
}
```

[↑ back to top](#table-of-contents)

### Place the first declaration on a new line after the opening brace

```css
/** bad */
.fooBlock {	display: block;
	color: #fff;
}

/** good */
.fooBlock {
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

Our [naming convention](https://github.com/procurios/HTML) should be sufficient to visualize relations between rules.

```css
/** bad */
.fooBlock {
	...
}

	.fooBlock__bar {
		...
	}

		.fooBlock__baz {

		}

/** good */
.fooBlock {
	...
}

.fooBlock__bar {
	...
}

.fooBlock__baz {

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
.fooBlock {
	overflow: hidden;
}

.fooBlock {
	overflow: hidden; /** This declaration needs some explanation */
}
```

[↑ back to top](#table-of-contents)

## Naming conventions

We use a BEM like naming convention. Read more about it in our [HTML style guide repository](https://github.com/procurios/HTML).

## Selectors

I quote [Harry Roberts](http://cssguidelin.es/#css-selectors):

> Poor Selector Intent is one of the biggest reasons for headaches on CSS projects. Writing rules that are far too greedy—and that apply very specific treatments via very far reaching selectors—causes unexpected side effects and leads to very tangled stylesheets, with selectors overstepping their intentions and impacting and interfering with otherwise unrelated rulesets.
>
> CSS cannot be encapsulated, it is inherently leaky, but we can mitigate some of these effects by not writing such globally-operating selectors: **your selectors should be as explicit and well reasoned as your reason for wanting to select something**.

### Use classes to select elements

The reasoning behind using only classnames to select elements:

- The CSS is _decoupled_: The dependency on the DOM is kept to a minimum. It makes it much easier to move your CSS around.
- The CSS is _isolated_: Classnames based on our naming convention are scoped to a specific `Block`.
- The CSS is _descriptive_: Classnames based on our naming convention tell developers stuff about what they're styling.

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

Don't worry about unavoidable exceptions to this rule. Use it as a rule of thumb.

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
```

[↑ back to top](#table-of-contents)

### Performance

Performance of CSS selectors is more interesting than it is important with today's browsers. If you want to know more about selector parsing, [start here](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Writing_efficient_CSS).

[↑ back to top](#table-of-contents)

## Specificity

### Don't use IDs

Not only are IDs non-reusable, they are also vastly more specific than any other selector, and therefore become specificity anomalies. Learn more about using IDs in CSS selectors [here](http://oli.jp/2011/ids/).

[↑ back to top](#table-of-contents)

### Use the least number of selectors required to style an element

```css
/** bad */
.fooBlock > .fooBlock__title {
	color: hotpink;
}

/** good */
.fooBlock__title {
	color: hotpink;
}
```

[↑ back to top](#table-of-contents)

### Use `!important` with care

The general rule is that `!important` is always a bad thing, but all rules have exceptions. [Harry Roberts](http://cssguidelin.es/#important) makes a distinction between proactive and reactive use of `!important`.

Proactive use of !important is when it is used before you’ve encountered any specificity problems; when it is used as a guarantee rather than as a fix. For example:

```css
.one-half {
    width: 50% !important;
}
```

Reactive use of `!important` is when it is used to combat specificity problems. In these situations, it is preferable that you investigate and refactor any offending rulesets to try and bring specificity down across the board.

[↑ back to top](#table-of-contents)

## Media queries

Place media queries as close to their relevant rule sets whenever possible. Don't bundle them all in a separate stylesheet or at the end of the document. Doing so only makes it easier for folks to miss them in the future. Here's a typical setup.

```css
.fooBlock {
	...
}

.fooBlock__avatar {
	...
}

@media (min-width: 480px) {
	.fooBlock {
		...
	}

	.fooBlock__avatar {
		...
	}
}
```

[↑ back to top](#table-of-contents)

## Element queries

An "element query" is like a media query, specifically the 'width'/'height' MQs, but they apply to the width/height of the element's container, rather than of the screen or device.

EQs aren't implemented by browsers yet. Tab Atkins explains [why EQs are difficult](http://www.xanthir.com/b4VG0):

> Element Queries (let's just call them EQs from here on) suffer from basic circular dependency issues.
>
> Here's a simple example: Say you have an element which is normally 100px wide, but it uses an EQ to say that if its container is less than 200px wide, the element becomes 500px wide. (This is silly, but bear with me.) If the container is explicitly sized (width: 150px; or the like), this is fine, but if the container is sized to its contents (float: left;, for example), then you have a circular dependency: if the element is 100px wide, the container is 100px wide, but that trigger the EQ, so the element is 500px wide, so the container is 500px wide, but that disables the EQ, so the element is 100px wide, so the container is 100px wide, etc.

In other words: browser vendors have some fundamental issues to deal with before EQs are shipped as native feature. Tab ends his overview with:

> So that's the state of Element Queries in 2014. We're not really any closer to having them than we were in 2013, but there's light on the horizon for a possible good solution.

That said, EQs are essential to create independant, isolated UI components. We've [published a Javascript library](https://github.com/procurios/ElementQueries) that takes care of this issue. The library contains [a comprehensive README](https://github.com/procurios/ElementQueries/blob/master/README.md) with clear instructions on how to implement and use element queries.