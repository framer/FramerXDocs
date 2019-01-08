# Code Components

## Requirements

Before you begin writing components, make sure you have an editor installed as Framer X does not come with a built in editor. Any editor that supports TypeScript will do, but we really like VSCode.

Make sure you setup [VSCode for external editing](../code/#setup).

{% hint style="info" %}
Framer X Beta only supports TypeScript but the general release will support plain ES6 too.
{% endhint %}

## React Components

As code components are just [React](https://reactjs.org/) components, it is useful to understand the bare basics of React, but not truly needed. As React components use [JSX](https://reactjs.org/docs/introducing-jsx.html) \(an HTML like markup language\) you can already write a component with just basic web development skills. Let's look at an example.

```typescript
import * as React from "react";

export class Example extends React.Component {
  render() {
    return <div style={{color: "blue"}}>Hello World!</div>
  }
}
```

This is the most basic React component. If you squint and look past the boilerplate \(like import and class\) you'll notice the render\(\) method returning something that looks a lot like HTML and CSS. Let's make it a bit more advanced and see if you can still recognize it.

```typescript
import * as React from "react";

export class Example extends React.Component {
  render() {
    return (
      <div style={{ color: "blue" }}>
        <h1>Hello World</h1>
        <p>
          Lorem ipsum
          <span onClick={() => alert("Hi")}>Click Me</span>
        </p>
      </div>
    );
  }
}
```

This should look very familiar if you have done web development before, and it's a full blown React component. From here, I would recommend to continue to learn React from their [excellent documentation](https://reactjs.org).

## Creating a Code Component

To create a new code component, go to the Components panel \(left side of the window\) and click "New Component". Then, select "from Code", pick a name \(no spaces\) and click "Create and Edit".

If you have an editor installed, it should now open up with a new boilerplate component which is purple and says "hello world". Go back to the Components panel in Framer X and drag a few onto the canvas. Note that they can have different positions and sizes. Every component on the canvas is an _instance_ of the code component.

Go back to your editor and change anything like the CSS or the hello world text. When you save the code file, you'll see that Framer automatically updates every instance to reflect the changes.

## Canvas Behavior

Components fully behave like you would expect in the Preview, but a bit different on the canvas. For example, scrolling and click handlers don't do anything on the canvas, as that would not mix well with manipulating and tools.

### Layout and Sizing

Every component rendered on the canvas or preview is wrapped in a Frame so they have the same layout rules as anything else on the canvas. Both the width and height are passed to the code component as props so you can use them.

```typescript
import * as React from "react";

export class Example extends React.Component<{width: number, height: number}> {
  render() {
    return (
      <div>
        {this.props.width} x {this.props.height}
      </div>
    );
  }
}
```

_Note: the TypeScript type annotations \(width, height\) are optional, but nice._

### Displaying Canvas Elements

Because the code determines the contents of code components, you cannot directly edit code component contents on the canvas. But often you'd like a code component to display something else from your canvas. For example, a Card component could render an image with some overlay that is somewhere else on your canvas. You can accomplish this in two ways.

#### Using props.children

React props are basically the attributes for a component to display, and one of those is a list of children, or it's contents \(like in the DOM or you see in the layer panel\). Normally these are determined from your code, but in Framer you can set any Frame on your canvas as children for your component. Let's look at an example.

```typescript
import * as React from "react";

export class Example extends React.Component<{width: number, height: number}> {
  render() {
    return (
      <div style={{width: this.props.width, height: this.props.height}}>
        <h1>Hello</h1>
        {this.props.children}
      </div>
    );
  }
}
```

Framer detects you are using the props.children property in your render method and automatically adds a connector to each instance of the component on your canvas \(a purple dot on the right side, like the scroll tool\). You can drag a connection from this connector to any Frame on the canvas and it will use it as its children to render.

_Hint: you can even override the props for the children by using_ `React.Children.map` _and_ `React.cloneElement` _methods._

#### Using canvas imports

You can easily import and use any named design component. The example below assumes you have a design component named `Row` .

```typescript
import * as React from "react";
import { Row } from "./canvas";

export class Test extends React.Component {
  render() {
    return <Row title="Koen" />;
  }
}
```

For a full overview see the [design components](design.md) guide.

## Exposing Controls

You can describe a custom interface for your components so component consumers can configure them on the canvas. The only thing you have to do is add a static `propertyControls` method to your class with a descriptor. It will use `defaultProps` for the defaults and try to type check your descriptors if you added type annotations for your props.

The example below is an excerpt of our iOS Alert component using a color, string and boolean control.

```typescript
import * as React from "react"
import { PropertyControls, ControlType } from "framer"

interface Props {
  title: string
  tintColor: string
  dimOverlay: boolean
}

export class Example extends React.Component<Partial<Props>> {

  static defaultProps = {
    title: "A short description of the actions goes here.",
    tintColor: "#007AFF",
    dimOverlay: true,
  }

  static propertyControls: PropertyControls<Props> = {
    title: { type: ControlType.String, title: "Title" },
    tintColor: { type: ControlType.Color, title: "Tint" },
    dimOverlay: { type: ControlType.Boolean, disabledTitle: "Hide", enabledTitle: "Show", title: "DimOverlay" },
  }

  render() { ... }
}
```

### Available Controls

Controls can be described by specifying one of the following types:

* Boolean
* Number
* String
* Color
* Image
* File
* Enum
* SegmentedEnum
* FusedNumber

#### Boolean Control

Booleans use a segmented control. The segment titles are `True` and `False` by default but these can be overridden using the `enabledTitle` and `disabledTitle`.

```typescript
interface BooleanControlDescription {
  type: ControlType.Boolean
  disabledTitle?: string
  enabledTitle?: string
}
```

#### Number Control

Number controls are displayed using an input field and a slider. The _min_ and _max_ values can be specified to constraint the output.

The default step size is 1. When a step size smaller then 1 is entered, the output will be floats.

When the unit type is set to %, the input field will display `10` as `10%`.

```typescript
interface NumberControlDescription {
  type: ControlType.Number
  max?: number
  min?: number
  step?: number
  unit?: string
}
```

#### String Control

String controls are displayed using a single line input field. A placeholder value can be set when needed.

```typescript
interface StringControlDescription {
  type: ControlType.String
  placeholder?: string
}
```

#### Color Control

Color controls are displayed using a color picker popover and a number input for the alpha.

```typescript
interface ColorControlDescription {
    type: ControlType.Color
}
```

#### Image Control

Image controls are displayed using an image picker that shows a small preview. The component receives an absolute URL during rendering.

```typescript
interface ColorControlDescription {
    type: ControlType.Image
}
```

#### File Control

File controls are displayed using a file picker that shows the file name after selecting a file. The component receives an absolute URL during rendering. The `allowedFileTypes` is an array containing all allowed file types, like so: `["json", "obj", "collada"]`

```typescript
interface ColorControlDescription {
  type: ControlType.File
  allowedFileTypes: string[]
}
```

#### Enum Control

An enum control displays a pop-up button with a fixed set of string values. The optionTitles can be set to have nicely formatted values for in the UI.

```typescript
interface EnumControlDescription {
  type: ControlType.Enum
  options: string[]
  optionTitles?: string[]
}
```

```typescript
interface Props {
  alignment: "start" | "center" | "end";
}

export class Stack extends React.Component<Props> {
  static defaultProps: Props = {
    alignment: "center"
  };

  static propertyControls: PropertyControls<Props> = {
    alignment: {
      type: ControlType.Enum,
      options: ["start", "center", "end"],
      optionTitles: ["Start", "Center", "End"],
      title: "Align"
    }
  };
}
```

#### Segmented Enum

A segmented enum control is displayed using a segmented control. Since a segmented control has limited space this only works for a tiny set of string values.

```typescript
interface SegmentedEnumControlDescription {
  type: ControlType.SegmentedEnum
  options: string[]
  optionTitles?: string[]
}
```

#### Fused Number

The fused number control is specifically created for border-radius, border-width, and padding. It allows setting a number value either using a single input or using four seperate number inputs. The user can switch from a single input to four by toggling a boolean.

```typescript
interface FusedNumberControlDescription {
  type: ControlType.FusedNumber
  toggleKey: string
  toggleTitles: [string, string]
  valueKeys: [string, string, string, string]
  valueLabels: [string, string, string, string]
  min?: number
}
```

```typescript
interface Props {
  padding: number;
  paddingPerSide: boolean;
  paddingTop: number;
  paddingRight: number;
  paddingBottom: number;
  paddingLeft: number;
}

export class Stack extends React.Component<Props> {
  static defaultProps: Props = {
    padding: 0,
    paddingPerSide: false,
    paddingTop: 0,
    paddingRight: 0,
    paddingBottom: 0,
    paddingLeft: 0
  };

  static propertyControls: PropertyControls<Props> = {
    padding: {
      type: ControlType.FusedNumber,
      splitKey: "paddingPerSide",
      splitLabels: ["Padding", "Padding per Side"],
      valueKeys: ["paddingTop", "paddingRight", "paddingBottom", "paddingLeft"],
      valueLabels: ["T", "R", "B", "L"],
      min: 0,
      title: "Padding"
    }
  };
}
```

### Hiding controls

Controls can be hidden by implementing the `hidden` function on the property description. The function receives an object containing the set properties and returns a boolean.

In the following example we hide the the `inCall` boolean control when the connected property is false.

```typescript
interface Props {
  connected: boolean
  inCall: boolean
}

export class NetworkComponent extends React.Component<Props> {
  static defaultProps: Props = {
    connected: true,
    inCall: false,
  }

  static propertyControls: PropertyControls<Props> = {
    connected: { type: ControlType.Boolean },
    inCall: {
      type: ControlType.Boolean,
      hidden(props) {
        return props.connected === false
      },
    },
  }
}
```

## Using the Framer Library

React components can do pretty much anything, but React itself is purely focused on composing interfaces from components. To do anything else, from managing application state to drawing graphs, it is very common to leverage other libraries.

The main use case of Framer X is prototyping, which typically includes flows, scrolling, animations and gestures. Framer X includes an optional library of helpers called Framer.js for these tasks. Using these is not required, you can use anything you like, but they should make interactive prototyping more enjoyable in most cases.

[Learn more about how to use the Framer.js library.](../code/framer.js/animation.md)

## Using External Libraries

WIP, not in Beta yet. But you can find hints in the package guide.

## Using Asset from Components

WIP, not in Beta yet.

## Editing Components from Packages

WIP, not in Beta yet. But you can right click any component and select "Copy Code".

