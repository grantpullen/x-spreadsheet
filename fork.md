# changes and dev info about this fork
### get changes from upstream
```git merge upstream/main```

### compile
```npm run-script build```

### replace upstream "original" version with forked version
remove the old version from the existing project (run below command in the project folder)

```npm uninstall x-spreadsheet```

add the forked version

```npm install grantpullen/x-spreadsheet```

alternately specify the version

```q```


## fork changes
* added ```setCellFocus(ri: number, ci: number): void;``` which is used to set the focus to the specified cell.
  - the parameter ri is the row number.
  - the parameter ci is the column number.

```javascript
const s = new spreadsheet("#x-spreadsheet-demo");
s.setCellFocus(3, 3);
```
* Added optional```customSettings?: {
  disableAutoIncrement?: boolean,
  copyEditableProperty?: boolean,
  };``` in constructor.
  - `disableAutoIncrement` is used to prevent auto increment of numbers in cells when dragging over a range can be disabled via boolean setting in the constructor named disableAutoIncrement.
  - `copyEditableProperty` is used to prevent propagation of the editable property when performing drag/copy & paste operations.
```javascript
const s  = new Spreadsheet('#sheetManagement', {
        customSettings: {
          disableAutoIncrement: true,
          copyEditableProperty: true,
        },
    });
```

* Exposed row insertion via ```insertRow(n: number): void```
  - rows are inserted before the current row.
  - the parameter n is the number of rows to be inserted.
  - a call to this function does not refresh the UI, (a call to reload can be used to force a refresh)
```javascript
const s = new spreadsheet("#x-spreadsheet-demo");
this.s.insertRow(1);
this.s.reload();
```

* Exposed row removal via ```deleteRow(): void```
  - the current row is the row which will be deleted.
  - a call to this function does not refresh the UI, (a call to reload can be used to force a refresh)
```javascript
const s = new spreadsheet("#x-spreadsheet-demo");
this.s.deleteRow();
this.s.reload();
```

* Exposed column insertion via ```inserColumn(n: number): void```
    - columns are inserted before the current column.
    - the parameter n is the number of columns to be inserted.
    - a call to this function does not refresh the UI, (a call to reload can be used to force a refresh)
```javascript
const s = new spreadsheet("#x-spreadsheet-demo");
this.s.insertColumn(1);
this.s.reload();
```

* Exposed column removal via ```deleteColumn(): void```
    - the current column is the column which will be deleted.
    - a call to this function does not refresh the UI, (a call to reload can be used to force a refresh)
```javascript
const s = new spreadsheet("#x-spreadsheet-demo");
this.s.deleteColumn();
this.s.reload();
```

* Exposed sheet reload via ```reload(): void```
```javascript
const s = new spreadsheet("#x-spreadsheet-demo");
this.s.insertColumn(1);
this.s.reload();
```
* Expose ability to set cell editable property via `cellEditable(canEdit: boolean): void;`
```javascript
const s = new spreadsheet("#x-spreadsheet-demo");
this.s.insertRow(1);
this.s.cellEditable(false);
this.s.reload();
```
