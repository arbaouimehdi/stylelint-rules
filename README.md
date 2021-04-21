<h1 align="center">Sass Codings Rules Summary</h1>

Forcing yourself to write a CSS code that follows a guideline can help the person ensue a list of good practices to write a CSS code reflecting a definite logic. Plus, it can adapt the whole team to a coding guideline to avoid incoherence across the entire code base.

I write the `.stylelintrc` list of practices to adapt to how I embrace the language; moreover, it can be tweakable depending on the context, and this is a summary of what can be done following these rules.

- Don't use IDs for styling.
- Don't Reference or style descendent elements in your class selectors
- Remove all trailing white space for your files
- Don't mix spaces with tabs for indentation
- Separate your code into a logical section using standard comment blocks.
- Leave one clear line under your section comments.
- CSS rules should be comma-separated but live on new lines
- Include a single space before the opening brace of a rule-set
- Include a single space after the colon of a declaration.
- Include a semi-colon at the end of every declaration in a declaration block
- Include a space after each comma in comma-separated property or function values.
- CSS Blocks should be separated by a single clear line
- Always use double quotes, quote attribute values in selectors
- Use lower-case and shorthand hex values
- Where allowed, avoid specifying units of zero values
- Disallow redundant values in shorthand properties.
- Never use `!important`
- Set properties explicitly
- Enforces `sass` variables in any CSS property using hex colors, except for the `currentColor` and `inherit` values.
- Sorts related property declarations by grouping together following the order (Sass Inheritance, Positioning, Box Model, Typography, Visual, Animation, Misc)
- Declare pseudo-classes with a single colon
- Declare pseudo-elements with a double colon
- Use `rem` units as primary unit type, This includes:
- Positioning: `top`, `right`, `bottom`, `left`
- Dimensions: `width`, `height`, `margin`, `padding`
- Font Size -->
Use `px` units as a primary unit type for the following properties
- Border widths: `border: 1px solid #bada55;`
- Line-height should be kept unitless. If you find you are using a line-height with a set unit type, try to think of alternative ways to achieve the same outcome. If it's a unique case that requires a specific `px` or `rem` unit, outline the reasoning with comments so that others are aware of its purpose.
- Avoid all use of magic numbers. Rethink the problem (`margin-top: 37px`)
- Aim for maximum depth of just 1 nested rule
- Components Syntax should follow `<componentName>[--modifierName|-descendantName]`
- `.componentName` must be written in camel case.
- `.componentName` class names as short as possible but as long as necessary.
- `--modifierName` must be written in camel case
- `--modifierName` must be separated from the component name by two hyphens
- `descendantName` must be written in camel case
- Use `componentName.is-stateOfComponent` for state-based modifications of components
- `is-stateOfComponent` must be camel case
- `is-stateOfComponent` should be used as an adjoining class
- Variables should be name such `[<componentName>[--modifierName][-descendantName]-]<propertyName>-<variableName>[--<modifierName>]`

Check the Coding [Guidelines](https://github.com/freemh/stylelint-rules/blob/main/.stylelintrc) that cover a thorough description of all the rules, plus the rules file [.stylelintrc](https://github.com/freemh/stylelint-rules/blob/main/.stylelintrc)
