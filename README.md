# CooklangEx

CooklangEx **ex**tends the base Cooklang Specification with the following feature syntaxes:

## Recipe Components
The recipe can be described using individual subcomponents by adding a Markdown Header Level 2 (`## Subcomponent`). There is only 1 subcomponent level in this specification (subcomponents cannot have their own subcomponents). These subcomponents can be referenced by prefixing the name with the same double hash (do not include a space). If the subcomponent name includes spaces, terminating curly braces are required.

The recipe can return to the top-level component using a markdown Horizontal Rule (`___` or `***` or `---`). Underscores are recommended (not enforced at the moment) for the Horizontal Rule character because Cooklang uses double-hyphen for comments.

## Ingredient Preparation
The method for preparing ingredients can be included in square brackets prior to the terminating curly braces. Curly braces are required to terminate the ingredient when the method of preparation is included.

## Temperatures
Temperatures follow the same convention as timers (including that they can be named), but substitutes the tilde (`~`) for an asterisk. Additionally, specific unit conversions (e.g.- for range temperatures) can be specified using the pipe (`|`) symbol inside the curly braces.

## General Measurements
Non-specific measurements can be denoted by using unadorned curly braces.

&nbsp;
---
&nbsp;

## Example
```
My Fake Pizza Recipe

## Dough
Combine @flour and @water in a #mixing bowl{}. Knead the dough and the wrap in #plastic wrap{}. Let rest in a refrigerator for at least ~{30%minutes}. Roll the dough on a @floured surface using #rolling pin{} to a thickness of about {1/8%inch}.

## Recommended Toppings
Melt @butter{1%tablespoon} in a #pan on *{medium|#4}. Saute the @red pepper[sliced]{1} and @small yellow onion[diced]{1/2} together in the pan.

___

Transfer the ##dough to a #pizza stone{}. Evenly spread @spaghetti sauce{1%cup} across the dough, stopping {1%inch} from the edge. Top first with @mozzarella cheese{} before adding the remaining ##recommended toppings{}. Cook in a preheated #oven at *preheat{450%F} for ~{25%minutes}.
```

&nbsp;
---
&nbsp;

## Rationale
### Recipe Components
Adding subcomponents provides a few benefits. First off, recipes are often separated into parts to begin with so this simply provides a uniformed syntax of labeling those distinct parts. Secondly, it can be used to automatically separate ingredents between parts of the recipe to aid in prep. Another benefit is the referencing syntax which can help add clarity to what parts should be combined at which point in the recipe. The referencing syntax can also be used to automatically add anchors/hyperlinks into the recipe for faster navigation.

The top-level return (horizontal rule) was included to aid programmatic formatting.

### Ingredient Preparation
This syntax was included to help compare ingredients across recipes and to also allow ingredients to be grouped for shopping purposes:

Two recipes may use the same ingredient, but one says to chop it while the other says to dice it. It's easier to compare the ingredients/shopping list for these two if the list if it only lists the item itself without including the method of preparation.

Similarly, a recipe my prepare an ingredient one way as part of cooking the dish and then a different way when adding the food as garnish to the finished platter. By separating out the preparation method you can create a shopping list for the recipe which only has a single line item for both entries.

### Temperatures and General Measurements
The Cooklang specification makes a provision for units as part of its ingredients syntax. One of the greatest benefits this provides is the ability to automatically convert the provided unit to a more suitable unit for yourself. It therefore makes sense to provide a syntax for other cooking-related units so that they can also be seamlessly converted.

The Temperatures include a prefix (mimicking timers) specifically so that they can be picked out for preheating ovens: the person preparing the meal often wants to know about this ahead of time so this syntax allows any display program to draw attention to it (such as including it at the top of the recipe).

General measures do not have a prefix because they normally are not interacted with or referenced outside of the line in which they appear.