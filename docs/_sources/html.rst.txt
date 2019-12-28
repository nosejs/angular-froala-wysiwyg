Displaying HTML
=====================================

To display content created with the froala editor use the froalaView directive.

`[froalaView]="editorContent"`

```html
<div [froalaEditor] [(froalaModel)]="editorContent"></div>
<div [froalaView]="editorContent"></div>
```
