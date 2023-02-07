# Heart Widget Input

Input has a custom solution in Heart, implemented to try to reduce fragmentation of input handling across numerous widgets, instead collating it all into a single asset, much like Epic's Enhanced Input Plugin.

## Why a Custom Solution?

The primary issue faced when handling input in UMG is that an input event, whether its a keyboard or mouse event, are bubbled through the widget hierarchy, from the most parent widget, until the leaf-most widget, and at any point, one of these widgets can choose to "reply" with either a Handled or Unhandled response (plus some additional information about the mouse sometimes). This is not inherently an issue; it is, in fact, amazing . . . most of the time. However, it results in input potentially being handled \*anywhere\* in the UI, which not only makes it difficult to track down issues, but makes implementing "generic" logic difficult as everything is tied to the particular widget class implementing the logic.

For organization purposes then, it makes sense to purposely limit oneself to \*not\* handling input arbitrarily, but instead use a centralized solution.

The CommonUI plugin in newer versions of Unreal solve this problem in its own way, with its **CommonUIInputData** system. There are two reasons Heart does not use this.&#x20;

1. It would require all users of Heart to also use CommonUI. I am not comfortable with this.
2. I simple don't like data table based workflows.

It's not that I dislike CommonUI, I use it quite extensively for both personal and work projects, and it has its selling points. But its input handling is quite obtuse, and not my style.

So what is my style? _Enhanced Input Plugin_. It defines input via individual assets, separates event handling from trigger definition neatly, and is nicely rebindable at runtime, something I cannot say about CommonUI (AFAIK, I'm no encyclopedia on the subject). But alas, it's only designed for use with Input Components, which are for handling _Actor_ input. So we cannot use it for UMG input.

## But What If We Could?

Heart Widget Input is a collection of classes built to work very similar to Enhanced Input, but tailored for use in UMG instead.

This allows us to do things such as allowing a Graph have an input command to delete a Node, without the graph _or_ input event having to care about what UMG particular widget is representing that Node at the time.

Heart Widget Input handlers can be reused across multiple graphs, but their keybinds differant for each, since triggers are defined in a separate asset.

The next few pages go into more detail about these classes, and how Heart Widget Input can be implemented in both C++ or BP.
