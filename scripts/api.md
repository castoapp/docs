# API Reference

## Overlays Class

### `static set(input: object, overlayNum: number, screenId: string): void`
Sets an overlay on a screen.

- `input`: The input object to be overlaid.
- `overlayNum`: The number of the overlay.
- `screenId`: The ID of the screen where the overlay will be set.

### `static unset(input: object, overlayNum: number, screenId: string): void`
Unsets an overlay from a screen.

- `input`: The input object to be un-overlaid.
- `overlayNum`: The number of the overlay to be removed.
- `screenId`: The ID of the screen from which the overlay will be removed.

## Autopilot Class

### `static start(): void`
Starts the autopilot.

### `static stop(): void`
Stops the autopilot.

### `static isActive(): boolean`
Checks if the autopilot is active.

### `static getScreenId(): string`
Returns the screen ID for autopilot.

## Source Class

### `Category(name: string): function`
- `name`: Category name.

### `Id(id: string): function`
- `id`: Input ID.

### `IdStartsWith(text: string): function`
- `text`: Text to check for the starting of the Input ID.

### `IdEndsWith(text: string): function`
- `text`: Text to check for the ending of the Input ID.

### `IdContains(text: string): function`
- `text`: Text to check for the presence in the Input ID.

### `Title(text: string): function`
- `text`: Title text.

### `TitleStartsWith(text: string): function`
- `text`: Text to check for the starting of the Input title.

### `TitleEndsWith(text: string): function`
- `text`: Text to check for the ending of the Input title.

### `TitleContains(text: string): function`
- `text`: Text to check for the presence in the Input title.

### `OverlayNumIs(num: number): function`
- `num`: Overlay number to check.

## Objects Class

### `static async get(source: function): Promise<object>`
- `source`: A filter function to fetch objects.

## Constants

### Is
- `InputAdded: string`: When an input has been added to a stage.
- `InputRemoved: string`: When an input has been removed from a stage.
- `AddedToOverlay: string`: When an input has been added to an overlay.
- `RemovedFromOverlay: string`: When an input has been removed from an overlay.

### Return
- `Input: string`: Constant for returning an input object.
- `Element: string`: Constant for returning a media element.
- `StageChild: string`: Constant for returning a stage child.

## Condition Class

### `constructor(options: object)`
- `options`: An object with the following properties:
  - `source: function`: A source function for filtering.
  - `is: string[]`: An array of event types.
  - `return: string[]`: An array of return types.

### `onExecute(cb: function)`
- `cb: function`: A callback function that is executed when the specified conditions are met. The callback function takes the following arguments:

  - `input`: The input object that triggered the event.
  - `element`: A media element associated with the event (if applicable).
  - `stageChild`: The stage child related to the event (if applicable).

The `cb` function is called when the defined conditions, such as specific events and source filters, are satisfied. It receives these arguments to allow for further actions or logic based on the event and specified conditions.