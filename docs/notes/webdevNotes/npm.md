npm
========================
## Installing dependencies from package.json

run `npm install .`

---

## Publishing to npm

[video by web dev simplified](https://www.youtube.com/watch?v=J4b_T-qH3BY)

1. Create a `package` folder, this will be where the final published thing will live. `cd` to this folder
2. Create a `package.json` file in the folder using `npm init`, can edit later.
    - `name` will be the name of the package
    - the `main` key in the `.json` should be the file name of the package entry point
    - prefixing `@muahchee/` in front of the package `name` will create a namespaced package, with "muahchee" being my username, prevent name clash
3. Test the package
    - add `module.exports = name of function/class to export` to the end of the entry point `js` file
    - run `npm link` in the command line, so if I install a test, it will be installed from this folder location
    - `cd` out of the folder and run `npm link name-of-package`, the package should show up in the `node_modules` folder.
    - test it out as normal
4. Publishing
    - `cd` into the `package` folder
    - run `npm login` to login to npm account
    - run `npm publish --access=public`. Namespaced packages are automatically assumed to be private packages, which we need to sign up for, thus the extra specification.
5. If you need to publish an update to the package, make sure to update the `version` key in the `package.json` file 