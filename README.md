# Welcome to my SCSS Samples Repository.

So, you may be asking yourself. Self, [What is SCSS](https://sass-lang.com/documentation/syntax#scss)?
I hope that link was able to answer your question :-)

In this repo you will find examples of:
 - [Mixin](https://sass-lang.com/documentation/at-rules/mixin)
 - [SCSS Variables](https://sass-lang.com/documentation/variables) 
 - [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)

And, the all important [some name].module.scss file.
More on that **[Here](https://medium.com/rubber-ducking/generating-typescript-definitions-for-css-modules-using-sass-461e33623ec2)**.
At the **top** of **the Global.module.scss file** you will see the following:
````scss
// Bring in our Variables:
@import './Variables';
````
You will notice that in the import statement i've left out the underscore. Thats because when you import it, it's not necessary to include the underscore. More on that **[Here](https://sass-lang.com/guide)** scroll down to the **Partials** section. 

Now, continuing down further in the file. You will see the **Export** statement. Now, you will see tons of articles and blogs that tell you to modify this or modify that. And don't even get me started on the rabbit hole I fell into when looking into webpack. No, no, no...
None of that is necessary. So, lets review a little code :-)

````scss
:export
{
   BaseFontFamily: #($BaseFontFamily);
}
````
This is where i'm hooking my **$BaseFontFamily** SCSS variable to a property that will be available upon import.

In the **ObjectExplorerBuilder.module.scss** file you can see how I'm referencing the CSS variables we exported using the [:root](https://developer.mozilla.org/en-US/docs/Web/CSS/:root) pseudo class in the **_Variables.scss** file.
````scss
// Import our functions:
@import "../../GlobalSCSS/Utility";

// Import our Global Variables:
@import "./environment/GlobalSCSS/Global.module.scss";
````
And you will see how to reference those varialbes.
````scss
  .WarningLabel_CloseIcon {
    cursor: pointer;
    font: hb-Map-Value(--BaseFontFamily);
````
Here i'm using my mixin function **hb-Map-Value**

How all this goes together:
Globals.module.scss imports the Variable.scss file. The main SCSS file for my custom object **ObjectExplorerBuilder.module.scss** imports 2 files: **Utility.scss** which has my mixins and **Global.module.scss** which has all my variables. Finally, ObjectExplorerBuilder.module.scss is imported into my custom object TypeScript file.

using:
- TypeScript 3.8.2
- Webpack 4.41.6
- Visual Studio Code (latest)

Please let me know if you have any questions.
