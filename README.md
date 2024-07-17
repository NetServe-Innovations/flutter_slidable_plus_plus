> ⚠️ This repository is a fork of the [original project](https://github.com/letsar/flutter_slidable) ([hash](https://github.com/letsar/flutter_slidable/commit/304330028117f6bff90bcda472fbd297258e0cb3)), where I implemented long-forgotten open PRs that the community had been awaiting for a long time. This is not a drop-in replacement as it introduces small breaking changes, but they are very easy to address.

-----

# flutter_slidable_plus

A Flutter implementation of slidable list item with directional slide actions that can be dismissed.

## Features

* Accepts start (left/top) and end (right/bottom) action panes.
* Can be dismissed.
* 4 built-in action panes.
* 2 built-in slide action widgets.
* 1 built-in dismiss animation.
* You can easily create custom layouts and animations.
* You can use a builder to create your slide actions if you want special effects during animation.
* Closes when a slide action has been tapped (overridable).
* Closes when the nearest `Scrollable` starts to scroll (overridable).
* Option to disable the slide effect easily.
* You can use custom widgets for icons

## Install

In the `pubspec.yaml` of your flutter project, add the following dependency:

```yaml
dependencies:
  flutter_slidable_plus: <latest_version>
```

In your library add the following import:

```dart
import 'package:flutter_slidable_plus/flutter_slidable_plus.dart';
```

## Getting started

Example:

```dart
Slidable(
  // Specify a key if the Slidable is dismissible.
  key: const ValueKey(0),

  // The start action pane is the one at the left or the top side.
  startActionPane: ActionPane(
    // A motion is a widget used to control how the pane animates.
    motion: const ScrollMotion(),

    // A pane can dismiss the Slidable.
    dismissible: DismissiblePane(onDismissed: () {}),

    // All actions are defined in the children parameter.
    children: const [
      // A SlidableAction can have an icon and/or a label.
      SlidableAction(
        onPressed: doNothing,
        backgroundColor: Color(0xFFFE4A49),
        foregroundColor: Colors.white,
        icon: Icon(Icons.delete),
        label: 'Delete',
      ),
      SlidableAction(
        onPressed: doNothing,
        backgroundColor: Color(0xFF21B7CA),
        foregroundColor: Colors.white,
        icon: Icon(Icons.share),
        label: 'Share',
      ),
    ],
  ),

  // The end action pane is the one at the right or the bottom side.
  endActionPane: const ActionPane(
    motion: ScrollMotion(),
    children: [
      SlidableAction(
        // An action can be bigger than the others.
        flex: 2,
        onPressed: doNothing,
        backgroundColor: Color(0xFF7BC043),
        foregroundColor: Colors.white,
        icon: Icon(Icons.archive),
        label: 'Archive',
      ),
      SlidableAction(
        onPressed: doNothing,
        backgroundColor: Color(0xFF0392CF),
        foregroundColor: Colors.white,
        icon: Icon(Icons.save),
        label: 'Save',
      ),
    ],
  ),

  // The child of the Slidable is what the user sees when the
  // component is not dragged.
  child: const ListTile(title: Text('Slide me')),
),
```

## Motions

Any `ActionPane` has a motion parameter which allow you to define how the pane animates when the user drag the `Slidable`.

### Behind Motion

The actions appear as if they where behind the `Slidable`:

![Behind Motion][behind_motion]

### Drawer Motion

Animate the actions as if they were drawers, when the `Slidable` is moving:

![Drawer Motion][drawer_motion]

### Scroll Motion

The actions follow the `Slidable` while it's moving:

![Scroll Motion][scroll_motion]

### Stretch Motion

Animate the actions as if they were streched while the `Slidable` is moving:

![Stretch Motion][stretch_motion]

### Controller

You can use ```SlidableController``` to open or close the actions programmatically:

```dart
final controller = SlidableController();

// ...

Slidable(
  controller: controller,
  // ...
);

// ...

// Open the actions
void _handleOpen() {
  controller.openEndActionPane();
  // OR
  //controller.openStartActionPane();
}

void _handleOpen() {
  controller.close();
}
```

## Contributions

Feel free to contribute to this project.

If you find a bug or want a feature, but don't know how to fix/implement it, please fill an [issue][issue].  
If you fixed a bug or implemented a feature, please send a [pull request][pr].

<!-- Links -->
[behind_motion]: https://raw.githubusercontent.com/vicenterusso/flutter_slidable_plus/assets/behind_motion.gif
[drawer_motion]: https://raw.githubusercontent.com/vicenterusso/flutter_slidable_plus/assets/drawer_motion.gif
[scroll_motion]: https://raw.githubusercontent.com/vicenterusso/flutter_slidable_plus/assets/scroll_motion.gif
[stretch_motion]: https://raw.githubusercontent.com/vicenterusso/flutter_slidable_plus/assets/stretch_motion.gif
