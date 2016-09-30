# ember-wizard

[![Build Status](https://travis-ci.org/alexlafroscia/ember-wizard.svg?branch=master)](https://travis-ci.org/alexlafroscia/ember-wizard)

> “Pay no attention to the man behind the curtain!”

## Features

- Provides an extremely generic way of describing a series of views that should be shown in succession
- Provides absolutely CSS styling and the bare minimum HTML to stay out of the way of your code

## Installation

```bash
ember install @alexlafroscia/ember-wizard
```

## Basic Usage

Using `ember-wizard` starts with creating a `step-manager`

```handlebars
{{#step-manager as |w|}}
  We'll put some cool stuff in here in a moment
{{/step-manager}}
```

Cool, right?  Ehh, it doesn't do much yet -- we need to add some steps

```handlebars
{{#step-manager as |w|}}
  {{#w.step name='a'}}
    This is the first step!
  {{/w.step}}

  {{#w.step name='b'}}
    This is the second step!
  {{/w.step}}
{{/step-manager}}
```

As you may have guessed, the first `w.step` component, `a`, will be visible initially, and `b` will be invisible.  Note that these names are important.  Why?  Because we need a way to transition between them!

```handlebars
{{#step-manager as |w|}}
  {{#w.step name='a'}}
    This is the first step!

    <button {{action w.transition-to 'b'}}>
      Next, please!
    </button>
  {{/w.step}}

  {{#w.step name='b'}}
    This is the second step!

    <button {{action w.transition-to 'a'}}>
      Wait, go back!
    </button>
  {{/w.step}}
{{/step-manager}}
```

The `step-manager` provides a [closure action][ember-closure-actions] that can be called with the name of a step to show that one, instead.  One of the neat features of `ember-wizard` is that there is no explicit order to the steps; show all of them, or only some. It's entirely up to you.

## Not-So-Basic Usage

The above examples show the basic idea, but there's more configuration (and power) available if you need it.  Head over to [the wiki][wiki] to read more about what `ember-wizard` can do!

[ember-closure-actions]: https://guides.emberjs.com/v2.8.0/templates/actions/
[wiki]: https://github.com/alexlafroscia/ember-wizard/wiki
