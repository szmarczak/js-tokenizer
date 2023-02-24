# js-tokenizer

Fast JavaScript tokenizer. Not published on NPM. [Single file](https://raw.githubusercontent.com/szmarczak/js-tokenizer/main/tokenizer.js). [MIT License](https://github.com/szmarczak/js-tokenizer/blob/main/LICENSE). If any of the below is a limitation, please use [SWC](https://github.com/swc-project/swc).

```
1) 2.5 times faster than lydell/js-tokens (7s vs 17s | 1000 iterations | jquery-3.6.3.js)
2) does not emit whitespace nor line separators
3) does not support automatic semicolon insertion
4) / after } is always considered a regular expression literal
5) does not support JSX
```

The output format is:

```js
['Punctuator',               startIndex, endIndex, string]
['SingleLineComment',        startIndex, endIndex, string]
['MultiLineComment',         startIndex, endIndex, string]
['RegularExpressionLiteral', startIndex, endIndex, string]
['StringLiteral',            startIndex, endIndex, string]
['NumericLiteral',           startIndex, endIndex, string]
['NoSubstitutionTemplate',   startIndex, endIndex, string]
['TemplateHead',             startIndex, endIndex, string]
['TemplateMiddle',           startIndex, endIndex, string]
['TemplateTail',             startIndex, endIndex, string]
['IdentifierName',           startIndex, endIndex, string]
['PrivateIdentifier',        startIndex, endIndex, string]
```

### Usage

```js
import { createTokenizer } from './tokenizer.js';

const tokenize = createTokenizer();
const code = `console.log('Hello, world!');`;

for (const token of tokenize(code)) {
    console.log(token);
}
```
