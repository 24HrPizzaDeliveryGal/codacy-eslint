# jquery-ember-run

:white_check_mark: The `"extends": "plugin:ember/recommended"` property in a configuration file enables this rule.

Don’t use jQuery without the Ember Run Loop.

Using plain jQuery invokes actions out of the Ember Run Loop. In order to have a control on all operations in Ember, it's good practice to trigger actions in run loop.

## Examples

Examples of **incorrect** code for this rule:

```js
import $ from 'jquery';

$('#something-rendered-by-jquery-plugin').on('click', () => {
  this._handlerActionFromController();
});
```

Examples of **correct** code for this rule:

```javascript
import $ from 'jquery';
import { bind } from '@ember/runloop';

$('#something-rendered-by-jquery-plugin').on(
  'click',
  bind(this, this._handlerActionFromController)
);
```
