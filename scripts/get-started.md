# Getting Started

<p>Writing a script with Scripts Engine is very easy. Just take the example below and modify it to your needs based on the <a href="/#/scripts/api">API Reference</a>.</p>

```js
// Add a condition to script
const condition = new Condition({
  source: Source.Category('video'), // All inputs with the "video" category
  is: [Is.InputAdded], // When the input was added to the stage
  return: [Return.Element], // Return media element to arguments
});

condition.onExecute((element) => {
  // Do something. For example, turn off the autopilot
  Autopilot.stop();
});
```

# Examples

<b>Put the logo on 3 overlay of autopilot stage when an input starts that has "Movie" in its name:</b>
```js
(async () => {
  const logo = await Objects.get(Source.TitleContains('Logotype')); // We're looking for a logo input by "Logotype" in name

  // Add a condition to script
  const condition = new Condition({
    source: Source.TitleContains('Movie'), // All inputs with "Movie" in their names
    is: [Is.InputAdded], // When the input was added to the stage
    return: [Return.Element], // Return media element
  });

  condition.onExecute(() => {
    Overlays.set(
      logo, // Logo
      3, // Overlay Num
      Autopilot.getScreenId() // Autopilot Stage ID
    );
  });
})();
```

<b>Remove the logo from the 3 overlay of the autopilot scene when the input that has "Movie" in the title disappears:</b>
```js
(async () => {
  const logo = await Objects.get(Source.TitleContains('Logotype')); // We're looking for a logo input by "Logotype" in name

  // Add a condition to script
  const condition = new Condition({
    source: Source.TitleContains('Movie'), // All inputs with "Movie" in their names
    is: [Is.InputRemoved], // When the input was been removed to the stage
    return: [Return.Input], // Return input object
  });

  condition.onExecute(() => {
    Overlays.unset(
      logo, // Logo
      3, // Overlay Num
      Autopilot.getScreenId() // Autopilot Stage ID
    );
  });
})();
```