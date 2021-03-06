<!-- Links in /docs/documentation should NOT have `.md` at the end, because they end up in our wiki at release. -->
**Documentation below is deprecated and we no longer accept PRs to improve this.**

# Include [Bootstrap](http://getbootstrap.com/)

[Bootstrap](http://getbootstrap.com/) is a popular CSS framework which can be used within an Angular project.
This guide will walk you through adding bootstrap to your Angular CLI project and configuring it to use bootstrap.

## Using CSS

### Getting Started

Create a new project and navigate into the project

```
ng new my-app
cd my-app
```

### Installing Bootstrap

With the new project created and ready you will next need to install bootstrap to your project as a dependency.
Using the `--save` option the dependency will be saved in package.json

```sh
npm install bootstrap --save
```

### Configuring Project

Now that the project is set up it must be configured to include the bootstrap CSS.

- Open the file `angular.json` from the root of your project.
- Under the property `projects` find your project.
- Inside `architect.build.options` locate the `styles` property.
- This property allows external global styles to be applied to your application.
- Specify the path to `bootstrap.min.css`

  It should look like the following when you are done:
  ```json
  "build": {
    "options": {
      "styles": [
        "../node_modules/bootstrap/dist/css/bootstrap.min.css",
        "styles.css"
      ],
    }
  }
  ```

**Note:** When you make changes to `angular.json` you will need to re-start `ng serve` to pick up configuration changes.

### Testing Project

Open `app.component.html` and add the following markup:

```html
<button class="btn btn-primary">Test Button</button>
```

With the application configured, run `ng serve` to run your application in develop mode.
In your browser navigate to the application `localhost:4200`.
Verify the bootstrap styled button appears.

## Using SASS

### Getting Started

Create a new project and navigate into the project

```
ng new my-app --style=scss
cd my-app
```

### Installing Bootstrap

```sh
npm install bootstrap --save
```

### Configuring Project

Create an empty file `_variables.scss` in `src/`.

If you are using `bootstrap-sass`, add the following to `_variables.scss`:

```sass
$icon-font-path: '../node_modules/bootstrap-sass/assets/fonts/bootstrap/';
```

In `styles.scss` add the following:

```sass
@import 'variables';
@import '../node_modules/bootstrap/scss/bootstrap';
```

### Testing Project

Open `app.component.html` and add the following markup:

```html
<button class="btn btn-primary">Test Button</button>
```

With the application configured, run `ng serve` to run your application in develop mode.
In your browser navigate to the application `localhost:4200`.
Verify the bootstrap styled button appears.
To ensure your variables are used open `_variables.scss` and add the following:

```sass
$primary: red;
```

Return the browser to see the font color changed.
