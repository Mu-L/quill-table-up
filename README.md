# quill-table-up

Enhancement of quill table module

[demo](https://zzxming.github.io/quill-table-up/)

## Why

Quill2.0 supports table related APIs, but unfortunately it did not complete UI operations, so this module is available to solve this problem.

This module is only an ui extension of the basic table module, without adding any new APIs.

## Usage

1. Install

```sh
npm install quill-table-up
```

```js
import Quill from 'quill';
import TableUp from 'quill-table-up';
import 'quill-table-up/index.css';
// import 'quill-table-up/table-creator.css'  // If using the default customSelect option. You need to import this css

Quill.register({ 'modules/tableUp': TableUp }, true);

const quill = new Quill('#editor', {
  // ...
  modules: {
    //  ...
    toolbar: [
      // ...
      [{ table: [] }] // use picker to enable the customSelect option
    ],
    tableUp: {},
  },
});

```

### Options

| attribute    | description                                                                                                              | type                                    |
| ------------ | ------------------------------------------------------------------------------------------------------------------------ | --------------------------------------- |
| customSelect | Custom table size selector. You can use the argument to insert any size table. It’s only enable when table is a `picker` | `(tableModule: TableUp) => HTMLElement` |
| texts        | The text used in the module                                                                                              | `TextMap`                               |
| isCustom     | Use input to input the table size                                                                                        | `boolean`                               |
| selection    | The options for table select module                                                                                      | `TableSelectionOptions`                 |

```ts
interface TextMap {
  customBtnText?: string;
  confirmText?: string; // input confirm button text
  cancelText?: string; // input cancel button text
  rowText?: string; // input row label text
  colText?: string; // input column label text
}

interface ToolOption {
  name: string; // tool name
  icon: string; // icon string
  tip?: string; // tool tip text
  handle: (tableModule: TableUp) => void;
};
interface ToolOptionBreak {
  name: 'break'; // when name is break, tool will insert a separator
}
type Tool = ToolOption | ToolOptionBreak;
interface TableSelectionOptions {
  selectColor: string; // select border color
  tools: Tool[]; // api button
}
```
