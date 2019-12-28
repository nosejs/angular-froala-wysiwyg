用法
=====================================

选项
--------------------

您可以通过编辑选项输入（可选）。

.. code::

   [froalaEditor]='options'

你可以通过任何现有的Froala选项。 请参考 `Froala文档 <https://www.froala.com/wysiwyg-editor/docs/options>`_ 查看所有可用的选项列表:

.. code:: typescript

   public options: Object = {
     placeholderText: 'Edit Your Content Here!',
     charCounterCount: false
   }

其他选项用于:

* **immediateAngularModelUpdate**: (default: false) 这个选项只要一键在编辑器发布同步角模型。
请注意，它可能会影响性能。



事件和方法
-----------------------------

事件可以通过与选择，具有重要事件和对象，其中的关键是事件的名称和值是回调函数。

.. code:: typescript

   public options: Object = {
     placeholder: "Edit Me",
     events : {
       'focus' : function(e, editor) {
         console.log(editor.selection.get());
       }
     }
   }


使用从回调可以调用编辑方法的参数编辑器实例作为 `方法的文档 <http://froala.com/wysiwyg-editor/docs/methods>`_ 中描述.

Froala事件在 `事件文档 <https://froala.com/wysiwyg-editor/docs/events>`_ 中描述.

模型
-----------------------------

所见即所得的HTML编辑器内容模型。

.. code::

   [(froalaModel)]="editorContent"

经过初步内容:

.. code:: typescript

  public editorContent: string = 'My Document\'s Title'


用在其他地方的内容:

.. code:: html

  <input [ngModel]="editorContent"/>
  <input [(ngModel)]="editorContent"/>
  <!-- For two way binding -->


其他双向绑定示例:

.. code:: html

  <div [froalaEditor] [(froalaModel)]="editorContent"></div>
  <div [froalaEditor] [(froalaModel)]="editorContent"></div>


与活性形式使用它:

.. code:: html

  <form [formGroup]="form" (ngSubmit)="onSubmit()">
    <textarea [froalaEditor] formControlName="formModel"></textarea>
    <button type="submit">Submit</button>
  </form>


如果你想使用双向绑定，以显示在其他地方的表单模型必须包括 `[（froalaModel）]`:

.. code:: html

  <form [formGroup]="form" (ngSubmit)="onSubmit()">
    <textarea [froalaEditor] formControlName="formModel" [(froalaModel)]="form.formModel"></textarea>
    <div [froalaView]="form.formModel"></div>
    <button type="submit">Submit</button>
  </form>


如果你想换froalaEditor指令到支持活性形式，请参阅从演示 `froala.component.ts <https://github.com/froala/angular-froala-wysiwyg/blob/master/demo/src/app/froala.component.ts>`_ 一个组成部分。

扩展功能
-----------------------------

您可以通过添加像波纹管自定义按钮来扩展功能:

.. code:: typescript

  // Import Froala Editor.
  import FroalaEditor from 'froala-editor';

  // We will make usage of the Init hook and make the implementation there.
  import { Component, OnInit  } from '@angular/core';

  @Component({
    selector: 'app-demo',
    template: `<div class="sample">
                <h2>Sample 11: Add Custom Button</h2>
                <div [froalaEditor]="options" [(froalaModel)]="content" ></div>
              </div>`,

  export class AppComponent implements OnInit{

    ngOnInit () {
      FroalaEditor.DefineIcon('alert', {NAME: 'info'});
      FroalaEditor.RegisterCommand('alert', {
        title: 'Hello',
        focus: false,
        undo: false,
        refreshAfterCallback: false,

        callback: () => {
          alert('Hello!', this);
        }
      });
    }

    public options: Object = {
      charCounterCount: true,
      toolbarButtons: ['bold', 'italic', 'underline', 'paragraphFormat','alert'],
      toolbarButtonsXS: ['bold', 'italic', 'underline', 'paragraphFormat','alert'],
      toolbarButtonsSM: ['bold', 'italic', 'underline', 'paragraphFormat','alert'],
      toolbarButtonsMD: ['bold', 'italic', 'underline', 'paragraphFormat','alert'],
    };
  }

特殊标签
-----------------------------

您也可以使用编辑器上** ** IMG ** **按钮，输入** **和** A **标签:

.. code:: html

  <img [froalaEditor] [(froalaModel)]="imgObj"/>


该模型必须包含您的特殊标签的属性的对象。例:

.. code:: typescript

  public imgObj: Object = {
    src: 'path/to/image.jpg'
  };


作为属性使用过程中改变froalaModel将发生变化。

* froalaModel可以包含命名** **的innerHTML一个特殊的属性，其插入的innerHTML在元件: 如果你正在使用的“按钮”标签，你可以指定按钮上的文字是这样:

.. code:: typescript

  public buttonModel: Object = {
    innerHTML: 'Click Me'
  };


随着按钮文本由编辑修改，** **的innerHTML从ButtonModel的模型属性也将被修改。



特殊标签的特定选项
-------------------------------------------

* **angularIgnoreAttrs**: (default: null) 此选项是要忽略的属性的数组时，编辑器将更新froalaModel:

.. code:: typescript

  public inputOptions: Object = {
    angularIgnoreAttrs: ['class', 'id']
  };

