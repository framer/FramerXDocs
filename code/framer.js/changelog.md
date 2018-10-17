# Changelog

## 0.8.1

2018-10-16

### Improved

-   Performance of `Data` objects
-   Overlay transitions can have a custom backdrop color
-   Scroll components support mouse-wheel scrolling by default


## 0.8.0

2018-09-18

### Improved

-   SVG component is now compatible with Stack layout

## 0.7.13

2018-09-17

### Fixed

-   Removed `debugger` statement

## 0.7.12

2018-09-14

### Added

-   `resource.url()` for referencing resources inside your project
-   Property control types for files (`ControlType.File`) and images (`ControlType.Image`)

### Improved

-   Display of errors in Components

### Fixed

-   Setting width in percentages for Design Components in Code
-   Scrolling animation with velocity

## 0.7.11

2018-09-07

### Improved

-   Internal changes for device rendering

## 0.7.10

2018-09-04

### Improved

* Interpolation of objects and colors

### Fixed

* Scrolling on touch devices
* Copy CSS for Stacks
* Transition of Navigation components

## 0.7.9

2018-08-31

### Improved

* Scaling font size for components with erros

### Fixed

* Rendering of shadows in Shapes

## 0.7.8

2018-08-29

### Added

* Fade transition for Navigation component

## 0.7.7

2018-08-28

### Fixed

* Bug in animation / interpolation API

## 0.7.6

2018-08-28

### Added

* Animation of colors

### Improved

* Importing Design Components in Code
* Animation API has more consistent option handling

### Fixed

* Empty state of Stack component
* Off-pixel rendering of Frame in some cases

## 0.7.5

2018-08-21

### Improved

* Generic types of `Override`

### Fixed

* Sorting UI of Stacks

## 0.7.4

2018-08-21

### Added

* Bezier curve animations

## 0.7.3

2018-08-20

### Added

* Support for OverrideFunctions for Design Components used in code

### Improved

* Skip invisible stack items during layout
* Renamed FusedNumber option splitKey to toggleKey

### Fixed

* Handling of Animatable properties in Stack
* Rerun OverrideFunction on rerender

## 0.7.2

2018-08-20

### Improved

* Fix FrameProperties type of Default Override type

## 0.7.1

2018-08-20

### Improved

* Made Animatable.set\(\) also accepts Animitable values
* Default Override type to FrameProperties

## 0.7.0

2018-08-20

### Improved

* Rename FramerFunction to Override

## 0.6.1

2018-08-16

### Added

* onClick, onMouseDown and onMouseUp as event handlers

### Fixed

* Setting default stack properties in package.json

## 0.6.0

2018-08-16

Bump version to 0.6 to avoid nmp registry conflicts in the future

### Fixed

* Make Stack background transparent by default

## 0.2.0

2018-08-15

### Improved

* Better typing of Data function

## 0.1.34

2018-08-15

### Added

* Added private API for CSS exporting from a component

### Improved

* Cleaned up CSS generation

## 0.1.33

2018-08-15

### Improved

* Made a deprecated PropertyStore available again

## 0.1.32

2018-08-15

### Fixed

* Bug where Animatable transactions would not work well together with ObservableObjects

## 0.1.31

2018-08-14

### Added

* Support for importing Design Components in code

## 0.1.30

2018-08-13

### Improved

* Change boolean control titles `enabled` and `disabled` to `enabledTitle` and `disabledTitle`

## 0.1.29

2018-08-13

### Property Controls

* `unit` type for number inputs \(e.g. %\)
* `step` allows numbers to be floats
* `placeholder` for string inputs
* `hidden` function allows controls to be hidden

## 0.1.28

2018-08-09

### Added

* `Data` function to create observable object that rerenders

### Fixed

* `animate()` function updates objects with multiple Animatable values only once per animation tick

## 0.1.27

2018-08-1

Initial Beta 1 release

