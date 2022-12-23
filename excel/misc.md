# Misc

## `indirect`

`index()` treats the value of a cell as a reference. e.g. if cell B3 has a value `B10`, then: `row(indirect(B3))=10`


## `hyperlink`

`=hyperlink(link_location, visible_name)` embeds a link in a cell.

```
=hyperlink("[C:\My Documents\Report.xlsx], "Open report")
```

If a sheet is named "Door1", and this name is given in cell B3, be careful of the quotes:
```
=hyperlink("#'"&B3&"'!A1, "Jump to Door")
```

## `webservice`, `filterxml`

`webservice` is used to retrive information from an API in real time. `filterxml` is used to retrive a specific piece of information for a given "xpath".