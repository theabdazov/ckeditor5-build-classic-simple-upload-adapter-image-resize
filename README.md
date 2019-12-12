#### Note:

**This is a custom build of CKEditor 5 with Simple Upload Adapter and Image Resize Plugins**
>It is important that you use the stable branch of a build, not the master branch. The master branch might contain changes which are not yet compatible with the versions of CKEditor 5 source packages that were published on npm.

>The ckfinder and easyimage plugins has been removed

## Documentation

Please check CKEditor 5 Editor official documentation:

-   [Documentation](https://ckeditor.com/docs/ckeditor5/latest/builds/guides/overview.html)
-   [Basic API](https://ckeditor.com/docs/ckeditor5/latest/builds/guides/integration/basic-api.html)
-   [Configuration](https://ckeditor.com/docs/ckeditor5/latest/builds/guides/integration/configuration.html)
-   [Creating custom builds](https://ckeditor.com/docs/ckeditor5/latest/builds/guides/development/custom-builds.html)
-   [Angular](https://ckeditor.com/docs/ckeditor5/latest/builds/guides/integration/frameworks/angular.html)

## Quick start

### Angular

Installation

```bash
npm i @ckeditor/ckeditor5-angular
npm i ckeditor5-build-classic-simple-upload-adapter-image-resize
```

Import the CKEditorModule module
```js
//...
import { CKEditorModule } from '@ckeditor/ckeditor5-angular';
 
@NgModule({
  imports: [
    //... 
    CKEditorModule
  ],
  declarations: [AppComponent],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

```js
import {Component} from '@angular/core';
import {CKEditor5} from '@ckeditor/ckeditor5-angular';
import ClassicEditor from 'ckeditor5-build-classic-simple-upload-adapter-image-resize';

@Component({
    selector: 'app-root',
    template:  `<ckeditor [editor]="editor" [config]="config"></ckeditor>`,
    styles: [``],
})
export class AppComponent {

  editor = ClassicEditor;

  config: CKEditor5.Config = {
    image: {
      // image plugin config
      toolbar: [ 'imageTextAlternative', '|', 'imageStyle:alignLeft', 'imageStyle:full', 'imageStyle:alignRight' ],
      styles: [
        'full',
        'alignLeft',
        'alignRight'
      ]
    },
    simpleUpload: {
      // The URL that the images are uploaded to.
      uploadUrl: "http://example.com",
      // Headers sent along with the XMLHttpRequest to the upload server.
      headers: {
       "X-CSRF-TOKEN": "CSFR-Token",
        Authorization: "Bearer <JSON Web Token>"
      }
    }
  };
}
```

### JS

Installation

```bash
npm i ckeditor5-build-classic-simple-upload-adapter
```

```js
import ClassicEditor from 'ckeditor5-build-classic-simple-upload-adapter';

// Or using the CommonJS version:
// const ClassicEditor = require('ckeditor5-build-classic-simple-upload-adapter');

ClassicEditor
  .create(document.querySelector('#editor'), {
  simpleUpload: {
      // The URL that the images are uploaded to.
      uploadUrl: "http://example.com",

      // Headers sent along with the XMLHttpRequest to the upload server.
      headers: {
        "X-CSRF-TOKEN": "CSFR-Token",
        Authorization: "Bearer <JSON Web Token>"
      }
    }
  })
  .then( editor => {
    window.editor = editor;
  })
  .catch( err => {
    console.error(err.stack);
  });
```

### HTML

Installation

```bash
npm i ckeditor5-build-classic-simple-upload-adapter
```

```html
<div id="editor">
  <p>This is the editor content.</p>
</div>
<script src="./node_modules/ckeditor5-build-classic-simple-upload-adapter/build/ckeditor.js"></script>
<script>
  ClassicEditor.create(document.querySelector("#editor"), {
    simpleUpload: {
      // The URL that the images are uploaded to.
      uploadUrl: "http://example.com/",

      // Headers sent along with the XMLHttpRequest to the upload server.
      headers: {
        "X-CSRF-TOKEN": "CSFR-Token",
        Authorization: "Bearer <JSON Web Token>"
      }
    }
  })
  .then(editor => {
    window.editor = editor;
  })
  .catch(err => {
    console.error(err.stack);
  });
</script>
```

**Note:** If you are planning to integrate CKEditor 5 deep into your application, it is actually more convenient and recommended to install and import the source modules directly (like it happens in `ckeditor.js`). Read more in the [Advanced setup guide](https://ckeditor.com/docs/ckeditor5/latest/builds/guides/integration/advanced-setup.html).
