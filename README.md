# pogo_box2d

[Box2D physics engine](https://box2d.org/) plugin to the [Pogo Game Engine](https://pub.dev/packages/pogo).

This currently uses Flame's [Box2D fork](https://github.com/flame-engine/box2d.dart) of Google's [Dart port of Java's Box2D port](https://github.com/google/box2d.dart).  box2d_flame pub.dev [here](https://pub.dev/packages/box2d_flame).

There is a simple example game that can be used as reference of how to use Box2D on Flame (0.6.x) [here](https://github.com/feroult/haunt).  How much of this applies to Pogo as well has yet to be determined.  Probably not much.

### Warning

Note that this is currently just a quick copy and error fix of how Flame was implementing Box2D.  **This has not been Pogo-ized yet.**  I haven't even tested it since Flame didn't have an example app for it.

This does not appear to be even remotely close to how I would build this, so expect major changes if I ever get around to refactoring this.  The current "components" found here are really entities and not components.  More likely, however, these will be dumped and replaced with a suite of true components (and maybe a mixin or something of the like).

### old details:

The whole concept of a box2d's World is mapped to the `Box2DComponent` component; every Body should be a `BodyComponent`, and added directly to the `Box2DComponent`, and not to the game list.

So you can have HUD and other non-physics-related components in your game list, and also as many `Box2DComponents` as you'd like (normally one, I guess), and then add your physical entities to your Components instance. When the Component is updated, it will use box2d physics engine to properly update every child.

## Adding the plugin to your Pogo project

Add the [pogo_box2d package](https://pub.dev/packages/pogo_box2d) dependency to your project's `pubspec.yaml`, for example (check your version number):

```yaml
dependencies:
  pogo_box2d: ^0.1.0
```

A plugin import is required in addition to the Pogo import in each source file that uses it:

```dart
import 'package:pogo/game_engine.dart';
import 'package:pogo_box2d/plugin.dart';
```
