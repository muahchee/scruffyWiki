npm
========================
## Installing dependencies from package.json

run `npm install .`

---

## Publishing to npm

[video by web dev simplified](https://www.youtube.com/watch?v=J4b_T-qH3BY)

[documentation](https://docs.npmjs.com/creating-node-js-modules)

1. Create a `package` folder, this will be where the final published thing will live. `cd` to this folder
2. Create a `package.json` file in the folder using `npm init`, can edit later.
    - `name` will be the name of the package
    - the `main` key in the `.json` should be the file name of the package entry point
    - prefixing `@muahchee/` in front of the package `name` will create a namespaced package, with "muahchee" being my username, prevent name clash
3. add `exports.name-of-module = class {}` to the main part of the entry point `js` file
4. Publishing
    - `cd` into the `package` folder
    - run `npm login` to login to npm account
    - run `npm publish --access=public`. Namespaced packages are automatically assumed to be private packages, which we need to sign up for, thus the extra specification.
5. If you need to publish an update to the package, make sure to update the `version` key in the `package.json` file 
---

## My npm modules

`npm install @muachee/module-name`

1. [@muahchee/dropdown-menu](https://www.npmjs.com/package/@muahchee/dropdown-menu)
2. [@muahchee/image-carousel](https://www.npmjs.com/package/@muahchee/image-carousel)