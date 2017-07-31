---
title: Using Scheme
layout: layout.html
---

# Using Scheme

The `Scheme` file is the default provided way to build User Interfaces. This is normal HTML with custom tags for OS.js components.

## Example

```html
<application-window data-id="SchemeTestWindow">
  <gui-vbox>
    <gui-vbox-container data-grow="0" data-shrink="1" data-basis="auto">

      <!-- Fragment within this file -->
      <gui-fragment data-fragment-id="MenuBar" />

    </gui-vbox-container>
    <gui-vbox-container data-grow="1" data-shrink="0" data-basis="auto" data-fill="true">

      <!-- Fragment from external file -->
      <gui-fragment data-fragment-external="scheme-part.html" />

    </gui-vbox-container>
  </gui-vbox>
</application-window>

<application-fragment data-id="MenuBar">
  <gui-menu-bar>
    <gui-menu-bar-entry data-label="LBL_FILE">
      <gui-menu data-id="SubmenuFile">
        <gui-menu-entry data-id="MenuClose" data-label="LBL_CLOSE"></gui-menu-entry>
      </gui-menu>
    </gui-menu-bar-entry>
  </gui-menu-bar>
</application-fragment>
```

## GUI Elements

GUI Elements are comprised of regular HTML, JavaScript and CSS.

### Common element methods

```js
/* DOM Manipulation and events */
.show()
.hide()
.empty()
.remove()
.append()
.appendHTML()
.querySelector()
.querySelectorAll()
.css('key' /*[, 'value'*/)
.on('name', function() {} /*, useCapture*/)

/* Attributes and values */
.set('key', 'value');
.get('key');

/* Inputs and views */
.focus()
.blur()

/* Data (like dropdowns and views) */
.clear();
.add('entry');
.add(['entry', 'entry']);
.remove('id' /*, 'key'*/);
.patch(['entry', 'entry'])
```

### Creating elements programatically

```js
//
// Normal
//
const guiElement = GUIElement.create('gui-element-name', {
  parameter: 'value'
});
parentElement.append(guiElement);

//
// Via DOM element
//
const guiElement = GUIElement.createFromNode(el);

//
// Using HTML
//
parentElement.appendHTML('<gui-element-name></gui-element-name>', optionalWinReference);
```

### Elements

Elements are speparated into these categories:

1. [Containers](#containers)
2. [Media](#media)
3. [Input](#input)
4. [Views](#views)
5. [Misc](#misc)

#### Containers

##### gui-vbox

A container with vertical (rows) that you can shrink/expand, also make content expand or fill.

![gui-vbox](/images/gui/gui-vbox.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>gui-vbox-container</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-vbox">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-hbox

A container with horizontal (columns) that you can shrink/expand, also make content expand or fill.

![gui-hbox](/images/gui/gui-hbox.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>gui-hbox-container</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-hbox">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-paned-view

A container with horizontal (columns) that you can shrink/expand, also make content expand or fill.

![gui-paned-view](/images/gui/gui-paned-view.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>gui-paned-view-container</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-paned-view">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-tabs

A tabbed container.

![gui-tabs](/images/gui/gui-tabs.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>gui-tab-container</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-tabs">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-toolbar

A container for holding buttons, etc.

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>all</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.toolbar">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-button-bar

Works like a toolbar, but is made for holding buttons with user-defined position(s).

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>all</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.button-bar">Overview</a></td>
    </tr>
  </tbody>
</table>

---

#### Media

##### gui-image
A normal image.

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-image">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-canvas
A paintable image (no actual painting included)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-canvas">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-audio
Play sounds or music.

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-audio">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-video
Display a video.

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-video">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-iframe
Display a iframe.

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-iframe">Overview</a></td>
    </tr>
  </tbody>
</table>

---

#### Input

##### gui-label
Display a normal text label.

![gui-label](/images/gui/gui-label.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-label">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-button
A button made for clicking!

![gui-button](/images/gui/gui-button.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-button">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-switch
A button, but works more like a light-switch.

![gui-switch](/images/gui/gui-switch.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-switch">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-radio
A radio button.

![gui-radio](/images/gui/gui-radio.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-radio">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-checkbox
A checbox.

![gui-checkbox](/images/gui/gui-checkbox.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-checkbox">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-select
A dropdown input.

![gui-select](/images/gui/gui-select.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-select">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-select-list
A selectable list.

![gui-select-list](/images/gui/gui-select-list.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-select-list">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-slider
A slider for giving a variable input.

![gui-slider](/images/gui/gui-slider.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-slider">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-text
A text entry box.

![gui-text](/images/gui/gui-text.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-text">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-password
A password entry box.

![gui-password](/images/gui/gui-password.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-password">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-textarea
A big text entry area.

![gui-textarea](/images/gui/gui-textarea.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-textarea">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-richtext
A big text entry area, with support for HTML.
<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-richtext">Overview</a></td>
    </tr>
  </tbody>
</table>

---

#### Views

##### gui-tree-view
A view with tree display (nested).

![gui-tree-view](/images/gui/gui-tree-view.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-tree-view">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-icon-view
A view with icon display.

![gui-icon-view](/images/gui/gui-icon-view.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-icon-view">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-list-view
A view with list display.

![gui-list-view](/images/gui/gui-list-view.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-list-view">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-file-view
A combination of all views above, with direct connection to the VFS. For file browsing.
<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-file-view">Overview</a></td>
    </tr>
  </tbody>
</table>

---

#### Misc

##### gui-progressbar
A box for showing progress.

![gui-progress](/images/gui/gui-progress.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-progress-bar">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-color-swatch
A box for selecting colors from a palette.

![gui-color-swatch](/images/gui/gui-color-swatch.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-color-swatch">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-menu-bar
A bar for showing menus with.

![gui-menu-bar](/images/gui/gui-menu-bar.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>gui-menu-bar-entry</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-menu-bar">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-menu
A menu box.
<table class="reference">
  <tbody>
    <tr>
      <td>Supported Parents</td>
      <td>gui-menu-bar-entry</td>
    </tr>
    <tr>
      <td>Allowed Children</td>
      <td>gui-menu-entry</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-menu">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-statusbar
A bar for showing statuses.
<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-statusbar">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-file-upload
Creates a button for uploading files.
<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-file-upload">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-input-modal
A textbox with an attached button designed for bringing up dialogs to set values.

![gui-input-modal](/images/gui/gui-input-modal.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-input-modal">Overview</a></td>
    </tr>
  </tbody>
</table>

##### gui-color-box
A button, but instead of text shows the color assigned.

![gui-color-box](/images/gui/gui-color-box.png)

<table class="reference">
  <tbody>
    <tr>
      <td>Allowed Children</td>
      <td>none</td>
    </tr>
    <tr>
      <td>API Reference</td>
      <td><a href="/doc/client/OSjs.GUI.Elements.html#.gui-color-box">Overview</a></td>
    </tr>
  </tbody>
</table>