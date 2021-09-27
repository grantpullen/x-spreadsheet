# Changes and dev info about this fork
### Get changes from upstream
```git merge upstream/main```

### Compile
```npm run-script build```

### Replace Upstream "original" version with forked version
Remove the old version from the existing project (run below command in the project folder)

```npm uninstall x-spreadsheet```

Add the forked version

```npm install grantpullen/x-spreadsheet```

alternately specify the version

```npm install grantpullen/x-spreadsheet#v1.0.0```


## Fork Changes
* added ```setCellFocus(ri: number, ci: number): void;``` which is used to set the focus to the specified cell.

```javascript
const s = new Spreadsheet("#x-spreadsheet-demo")
s.setCellFocus(3, 3);
```
* removed auto increment of numbers in cells when dragging over a range.
