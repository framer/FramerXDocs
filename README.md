# Framer X

## Framer X has launched. 

Please find our official documentation via [https://www.framer.com/docs](https://www.framer.com/docs) and our resources via [https://www.framer.com/resources](https://www.framer.com/resources). We are actively updating both the documentation and resources as we go, but feel more than welcome to reach out to [support@framer.com](mailto:%20support@framer.com) if you find anything missing.

## Welcome

Thanks for joining the beta program. This guide is very much a work in progress towards the final release. Feel free to send us feedback, or make suggestions on GitHub directly.

### The Best Way to Start; TLDR

* Read [how to think about Framer X](https://framer.gitbook.io/framer/#how-to-think-about-framer-x) and supported design work below.
* Read the [beta program page](introduction/beta/) on what to expect in Beta 1. _**Hint**: some of the code parts are still in progress \(code functions, state\), and being offline will cause some issues._
* Explore the canvas, automatic layout, styling, stacks, design components, flow and scroll interactions, using the store to install packages and build a simple React component yourself, optionally with some [custom properties](components/#adding-framer-interface-for-props) that you can configure from the Framer interface.

## How to Think About Framer X

Framer X is quite different from other design tools. It aims to **blend canvas and code,** as well as **design and development**, to support a new more natural and efficient way of designing digital products.

Framer X is more like [Unity](https://unity3d.com/unity/editor) than like Photoshop. An [**IDE**](https://en.wikipedia.org/wiki/Integrated_development_environment) **for design**, if you will. Framer X can do many different things from wire-framing to visual design to screen flows to design systems to interactive component programming. We expect most users to only use what they need based on their project or skill level.

Framer X is both the **most easy and most advanced** design tool. We think a subset of more advanced users will build components for everyone else, so the majority of users won’t write code, but visually compose interfaces with components built by others through the store. But if you enjoy writing code, Framer X will be the best environment to do so and we encourage everyone to explore it.

The idea behind Framer X is **not to generate code for you**, but instead to use the code you \(or someone else\) wrote. Auto generated code almost never ends up in production, so it's better to have a tool use the code that is being used. If you already have React components built, they should work in Framer X with minimal effort. That said, _everything_ you draw in Framer is a React component and exportable to `jsx`, `html` or static assets if you need it.

## Supported Design Workflows

The goal of Framer X is to support many types of workflows, and with that many types of users at different skill levels, but to never hold you back and even encourage you to explore more.

The list below is an example of parts of Framer X you would need for different design tasks. Make sure to check our [beta feature list](introduction/beta/#beta-features) to make sure what is available today.

**A. Wire-framing** – quickly visualize an interactive idea, layout, user flow and information architecture.

* **Interface:** login, signup, canvas, properties, tools, layers, components, store.
* **Canvas:** navigation, selection, editing.
* **Layout:** \(auto\) hierarchy, \(auto\) positioning, frames, images, text, stacks.

_No previous skills required._

**B. Visual Design** – explore styling options for layouts, create icons and artwork and produce high res assets for production with pixel level control.

* **Drawing:** shapes, path editing, styling, grouping, boolean operations.
* **Import / Export:** paste, Sketch paste, image exporting, SVG exporting, code export.

_Helpful to have: some experience with drawing tools, computer graphics._

**C. Interactive** – quickly turn visual parts into a prototype with navigation, different screens, advanced scrolling and some interactive components. All without code.

* **Preview:** window, frame selection, device, presentation mode, mobile preview, remote preview, inspector, print.
* **Interactive:** link, scroll, page.
* **Design Components:** panel, organization, search, master, instance, overrides, nesting, use from code.
* **Store:** browse, search, install, update, private company store.
* **Sharing:** cloud, web project.

_Helpful to know: HTML, CSS, web publishing._

**D. Expert interactive** – create real products, invent your own interactions with state, data, physics, user input and combine with any other JavaScript out there.

* **Code Components:** creation, editing, interface props, canvas children.
* **Code Functions:** creation, editing, state.
* **Code Library:** animation, interpolation, events, gestures, components.

_Helpful to know: JavaScript, React, motion graphics._

**E. Design Infra** – build and manage from components to entire design systems for teams, scale them to large organizations, integrate with production.

* **Packages:** publish, update, versioning, dependencies.

_Helpful to know: NPM, Yarn._

![](.gitbook/assets/framer%20%281%29.png)

