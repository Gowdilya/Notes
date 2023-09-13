

A _Decorator_ is a special kind of declaration that can be attached to a [class declaration](https://www.typescriptlang.org/docs/handbook/decorators.html#class-decorators), [method](https://www.typescriptlang.org/docs/handbook/decorators.html#method-decorators), [accessor](https://www.typescriptlang.org/docs/handbook/decorators.html#accessor-decorators), [property](https://www.typescriptlang.org/docs/handbook/decorators.html#property-decorators), or [parameter](https://www.typescriptlang.org/docs/handbook/decorators.html#parameter-decorators). Decorators use the form `@expression`, where `expression` must evaluate to a function that will be called at runtime with information about the decorated declaration.

For example, given the decorator `@sealed` we might write the `sealed` function as follows:

`   function sealed(target) {    // do something with 'target' ...  }   `

## Decorator Factories

If we want to customize how a decorator is applied to a declaration, we can write a decorator factory. A _Decorator Factory_ is simply a function that returns the expression that will be called by the decorator at runtime.

We can write a decorator factory in the following fashion:

`   function color(value: string) {    // this is the decorator factory, it sets up    // the returned decorator function    return function (target) {      // this is the decorator      // do something with 'target' and 'value'...    };  }   `

## [](https://www.typescriptlang.org/docs/handbook/decorators.html#decorator-composition)Decorator Composition

Multiple decorators can be applied to a declaration, for example on a single line:

`   @f @g x   `[Try](https://www.typescriptlang.org/play/#code/PTAEAEFMA8AdIE4EsC2kB2AXAhgGwCKQDGA9gtpmQM4BQIE6JAoggtTQGYCu6RmSJdKA4AKAJSgA3gF9OPPgKEBzcVNn0AtFqJdMWjTXAcIS0NCA)

On multiple lines:

`   @f  @g  x   `

When multiple decorators apply to a single declaration, their evaluation is similar to [function composition in mathematics](https://wikipedia.org/wiki/Function_composition). In this model, when composing functions _f_ and _g_, the resulting composite (_f_ ∘ _g_)(_x_) is equivalent to _f_(_g_(_x_)).

As such, the following steps are performed when evaluating multiple decorators on a single declaration in TypeScript:

1. The expressions for each decorator are evaluated top-to-bottom.
2. The results are then called as functions from bottom-to-top.

If we were to use [decorator factories](https://www.typescriptlang.org/docs/handbook/decorators.html#decorator-factories), we can observe this evaluation order with the following example:

`   `