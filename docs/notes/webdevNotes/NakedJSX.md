NakedJSX
========================

[https://nakedjsx.org/](https://nakedjsx.org/)
[https://nakedjsx.org/documentation/](https://nakedjsx.org/documentation/)

`npx nakedjsx jsx-working --out site/html --css-common site/styles/painting-failure.css --pretty` 

`jsx` files should be in a `src` folder

run on command line in `[jsx folder]` parent

`npx nakedjsx [jsx folder] --out [relative path to output folder] --css-common [relative path to css file]

"If you build it without the `--pretty` flag, the result is tightly packed and suitable for distribution"

you can only link one css file in the command line, for `reset.css` I'll import and use `Page.AppendCss(reset)`

Options:

    # Launch a hot-refresh development server
    --dev

    # Save the effective config to <pages-directory>/.nakedjsx.json
    --config-save

    # The build output will be placed here
    --out <path>

    # CSS to compile and compress along with extracted scoped css="..." JSX attributes
    --css-common <path-to-css-file>

    # Enable plugin and set its unique alias, for example: --plugin image @nakedjsx/plugin-asset-image
    --plugin <alias> <plugin-package-name-or-path>

    # Import path alias, eg. import something from '$SRC/something.mjs'
    --path-alias <alias> <path>

    # Make string data available to code, eg. import VALUE from 'KEY'
    --define <key> <value>

    # Don't create sourcemaps (which are normally enabled in dev mode and when debugger attached)
    --sourcemaps-disable

    # Create sourcemaps (which are normally disabled unless dev mode or when debugger attached)
    --sourcemaps-enable

    # Produce less log output
    --quiet

    # Format output HTML, CSS, and JavaScript. Warning: Looks better, but assumes whitespace around some HTML tags is not significant. Use --pretty-ish if that is a problem.
    --pretty

    # Format output HTML, CSS, and JavaScript, preserving whitespace around all HTML tags.
    --pretty-ish

    # Print basic help information and exit
    --help
