# React Native

* Framework for building Native Apps using React
* Types of apps:
  * Web: React, Angular, HTML, CSS, JS
  * Native: Swift, Java, Kotlin, Objective-C
  * Hybrid:  React Native, PhoneGap, Cordova, Xamarin, NativeScript
* Components:
  * Naming requirements: the first letter must be in upper case
  * Built-in Components:
    * View
      * 2 main uses: layout and styling. It's a container for other elements and can be used to create UI elements like borders and shapes
    * Text: just a label. It's not an input 
* Flex style attribute:
  * it represents the ratio of space that a component should take up along the primary axis
  * _Flex: 1._ The __component will expand to fill its parent
  * _Flex: 0._ The component will take only the minimum space required to display its content
* Layout:
  * 3 attributes can be used: flexDirection, justifyContent, aligItems
  * it also uses the box-model from CSS
  * Yoga layout engine
    * it mimics the flexbox used in browsers, but the defaults are different and it adds new features, like aspectRatio
  * flexDirection
    * defines the primary axis
    * child components are laid out along the primary axis
    * the orthogonal axis is called the secondary axis
    * possible values: column, row, column-reverse, and row-reverse
  * justifyContent
    * distribute the children along the primary axis
    * possible values \(distribute children...\):
      * flex-start:  at the start of the primary axis
      * flex-center: at the center
      * flex-end:: at the end
      * space-around: evenly adding space at the edges
      * space-between: evenly without space at the edges
  * alignItems
    * align children components along the secondary axis
    * possible values \(align children...\):
      * flex-start: at the start
      * flex-center: at the center
      * flex-end: at the end
      * stretch: make children fill height and width of the secondary axis
  * The whole view is _wrapped_ in a view with these defaults:
  * ```text
    {
        flexDirection: "column",
        justifyContent: "flex-start",
        alignItems: "stretch"
    }
    ```
* Styles
  * generally created after the component \(not sure I like this. Things should be defined before they're used\)
* Images
  * can be bundled with the app or download from the internet



