Manual Initialization
=====================================


Gets the functionality to operate on the editor: create, destroy and get editor instance. Use it if you want to manually initialize the editor.

.. code::

   (froalaInit)="initialize($event)"

Where `initialize` is the name of a function in your component which will receive an object with different methods to control the editor initialization process.

.. code:: typescript

  public initialize(initControls) {
    this.initControls = initControls;
    this.deleteAll = function() {
      this.initControls.getEditor()('html.set', '');
    };
  }


The object received by the function will contain the following methods:

- **initialize**: Call this method to initialize the Froala Editor
- **destroy**: Call this method to destroy the Froala Editor
- **getEditor**: Call this method to retrieve the editor that was created. This method will return *null* if the editor was not yet created

