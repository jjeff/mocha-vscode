# Mocha VS Code Extension

This a community Visual Studio Code extension for enabling developers to run and debug [Mocha](https://mochajs.org/) tests right within VS Code using the built-in test explorer.

> [!NOTE]
> This extension is in a fairly early development stage but mostly functional. But watch out for any bugs 😉
>
> Please provide feedback and discuss improvements over at https://github.com/CoderLine/mocha-vscode/discussions and https://github.com/CoderLine/mocha-vscode/issues

## Getting Started

To get started follow the [general Mocha documentation](https://mochajs.org/) to set up testing for your project using the Mocha command line. Then, [install this extension](https://marketplace.visualstudio.com/items?itemName=coderline.mocha-vscode).

This extension automatically discovers and works with the `.mocharc.js/cjs/yaml/yml/json/jsonc` files found in your workspace. It requires minimal to no extra configuration. It works by looking at test files in your JavaScript and TypeScript code.

## Configuration

- `mocha-vscode.extractSettings`: Configures how tests get extracted. You can configure:

  - The `extractWith` mode, that specifies if tests are extracted.
    - `evaluation-cjs` (default) Translate the test file to CommonJS and evaluate it with all dependencies mocked.
    - `evaluation-cjs-full` Translate the test file to CommonJS and fully evaluate it with all dependencies.
    - `syntax` Parse the file and try to extract the tests from the syntax tree.
  - The `extractTimeout` limiting how long the extraction of tests for a single file is allowed to take.
  - The `test` and `suite` identifiers the process extracts. Defaults to `["it", "test"]` and `["describe", "suite"]` respectively, covering Mocha's common interfaces.
  - The `hooks` identifiers to avoid Mocha executing stuff on test discovery. Defaults to `["before", "after", "beforeEach", "afterEach"]`.

- `mocha-vscode.debugOptions`: options, normally found in the launch.json, to pass when debugging the extension. See [the docs](https://code.visualstudio.com/docs/nodejs/nodejs-debugging#_launch-configuration-attributes) for a complete list of options.

- `mocha-vscode.env`: Additional environment variables set when executing tests. This is useful for setting things like `NODE_ENV`.

- `mocha-vscode.mochaPath`: Specifies the path to the Mocha executable. If not set, the extension will attempt to resolve the Mocha executable from the local `node_modules` directory.

## Example

To set the `mochaPath` setting, open your VS Code settings (`Cmd + ,` on Mac) and search for `mocha-vscode`. Set the `mochaPath` to the path of your Mocha executable.
