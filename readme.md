# VS Code ESM URL

This extension installs a TS Server plugin which adds partial support for URL
parts in the ESM `import` statements. Relative local file paths which include
`?search` or `#fragment` bits will have those stripped for the purposes of
module name resolution, resulting in the language service being able to trace
and infer types through module boundaries such as these:

`index.js`:
```javascript
// Click through `mod` or `mod.js` and see that it correctly jumps to `mod.js`
import mod from './mod.js?arg';

// Hover over `mod` and see that it correctly shows the inferred return type
console.log(mod());
```

`mod.js`
```javascript
export default function test() {
  return 'test';
}
```

The same thing works for TypeScript files, too!

Proper ESM URL support in TypeScript is probably months if not years away, this
extension fills the void until that is resolved. You can follow the progress
along here:

https://github.com/microsoft/TypeScript/issues/41730

## Installation

This extension is not in the VS Code Marketplace yet. To install it, clone this
repository, set up and run `vsce login` and then run `vsce package`.

https://code.visualstudio.com/api/working-with-extensions/publishing-extension#publishing-extensions

A VSIX file named `vscode-esm-url-0.0.1.vsix` will be spat out. Install this
VSIX file into your VS Code installation.

https://code.visualstudio.com/docs/editor/extension-gallery#_install-from-a-vsix
