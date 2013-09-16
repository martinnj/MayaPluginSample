MayaPluginSample
================

Repo to contain a sample Maya plugin with initialize, uninitialize functions
and a cmake build file for cross platform compilation.

Life of a Maya command plugin
================================

<ol start="0">
    <li>Maya calls the creator function which sets up an object that 
        contains the working code.</li>
    <li>The constructor runs, doing its work.</li>
    <li>The doIt function gets called, doing the actual work the
        command should do.</li>
    <li>Maya calls the "is undoable" function, if it returns false the
        destructor is called and the command object gets "destroyed".
        If it returns true however, Maya returns to normal working
        mode.</li>
    <li>object lives on in the background, if undo/redo is requested,
        the functions below gets called, if the plugin is unloaded,
        the destructor gets called.</li>
    <li>If the command gets pushed out of the buttom of the undo/redo
        stack, the destructor gets called.</li>
</ol>