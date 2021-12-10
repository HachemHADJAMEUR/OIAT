# OIAT

#Ceci est un outil développé pour l'inspection de l'état des attaches dans le tunnel 

## Structure of your template

```text
template_package
├── package.json (for your template package to be published on npm)
├── index.js
└── template_src (contains template files)
    ├── package.json
    ├── config.xml
    └── (files and folders that make up the template)
```

### Outside of `template_src`

All files outside of `template_src` are used to define parameters about the template. These files are not copied over at creation, so feel free to add a README or any other files outside of `template_src`.

#### index.js

`index.js` points to where the template exists. You'll see that `index.js` usually looks like:

```javascript
const path = require('path');

module.exports = {
    dirname : path.join(__dirname, 'template_src')
};
```

#### package.json

This `package.json` holds *information about the template itself* like its `name`, `version` etc. All templates should contain the keyword `"cordova:template"` so that the template is searchable on npm. For example:

```json
{
    "name": "cordova-example-template",
    "version": "1.0.0",
    "...": "...",
    "keywords": [
        "cordova:template"
    ]
}
```

### Inside of `template_src`

All files inside of `template_src` compose the template from which a user would desire in order to create their project. Everything in this folder is copied over to the created project.

The package.json in `template_src` should be filled with information that describes *the project that would be created from the template*.

If you want to include `.gitignore` files in your template, you have to name them `gitignore` (without a leading dot) instead. They will be renamed to `.gitignore` upon template expansion.
