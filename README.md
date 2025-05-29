# 🚀 Lesser-Known Flutter Tips & Tricks

Welcome to **Lesser-Known Flutter Tips & Tricks** – a curated collection of powerful yet often overlooked features in Flutter. These tips will help you write cleaner, more efficient, and more maintainable code while unlocking advanced capabilities of the framework.

Whether you're a beginner or an experienced Flutter developer, you'll likely find some new gems here!

---

## 📋 Table of Contents

- [1. WidgetsApp vs MaterialApp](#1-widgetsapp-vs-materialapp)
- [2. Safe setState with mounted](#2-safe-setstate-with-mounted)
- [3. Post-frame Callback](#3-post-frame-callback)
- [4. KeepAlive in Tab Views](#4-keepalive-in-tab-views)
- [5. InkWell vs GestureDetector](#5-inkwell-vs-gesturedetector)
- [6. Platform-aware Widgets](#6-platform-aware-widgets)
- [7. Flutter Inspector Power](#7-flutter-inspector-power)
- [8. Using Keys for List Optimization](#8-using-keys-for-list-optimization)
- [9. Context Extensions](#9-context-extensions)
- [10. Visibility Alternatives](#10-visibility-alternatives)


---

## 💡 1. WidgetsApp vs MaterialApp

Use `WidgetsApp` when you want full control over theming and don’t need Material or Cupertino widgets:

```dart
return WidgetsApp(
  color: Colors.blue,
  builder: (context, child) => YourCustomApp(),
);
```

---

## 🔒 2. Safe `setState` with `mounted`

Avoid calling `setState()` on unmounted widgets after async calls:

```dart
Future<void> loadData() async {
  await Future.delayed(Duration(seconds: 1));
  if (!mounted) return;
  setState(() {});
}
```

---

## 🧐 3. Post-frame Callback

Run code **after** the first frame is rendered – useful for animations, scrolling, etc.

```dart
WidgetsBinding.instance.addPostFrameCallback((_) {
  // First frame rendered
});
```

---

## 📌 4. KeepAlive in Tab Views

Prevent tab widgets from being disposed when switching tabs:

```dart
class MyTab extends StatefulWidget {
  @override
  _MyTabState createState() => _MyTabState();
}

class _MyTabState extends State<MyTab> with AutomaticKeepAliveClientMixin {
  @override
  bool get wantKeepAlive => true;

  @override
  Widget build(BuildContext context) {
    super.build(context); // Important
    return ...;
  }
}
```

---

## 🌊 5. InkWell vs GestureDetector

Use `InkWell` for material ripple effect (on top of a `Material` widget):

```dart
InkWell(
  onTap: () {},
  child: Padding(
    padding: EdgeInsets.all(16),
    child: Text("Click me"),
  ),
)
```

---

## 🍎 6. Platform-aware Widgets

Customize your UI for different platforms:

```dart
if (Theme.of(context).platform == TargetPlatform.iOS) {
  return CupertinoButton(...);
} else {
  return ElevatedButton(...);
}
```

---

## 🕵️ 7. Flutter Inspector Power

Use **"Select Widget Mode"** in Flutter DevTools to inspect your app and jump directly to the corresponding widget in your code.

---

## 🗑️ 8. Using Keys for List Optimization

Preserve scroll position and improve performance with `ValueKey`:

```dart
ListView.builder(
  itemCount: items.length,
  itemBuilder: (context, index) {
    return ListTile(
      key: ValueKey(items[index].id),
      title: Text(items[index].name),
    );
  },
);
```

---

## ✨ 9. Context Extensions

Add useful shortcuts to `BuildContext` with Dart extensions:

```dart
extension ContextExtensions on BuildContext {
  Size get screenSize => MediaQuery.of(this).size;
  bool get isDarkMode => Theme.of(this).brightness == Brightness.dark;
}
```

---

## 🧹 10. Visibility Alternatives

Instead of using the `Visibility` widget:

```dart
widget.shouldShow
  ? YourWidget()
  : const SizedBox.shrink();
```

This reduces unnecessary widget rebuilds.

---

## 📣 Contribute

Have more hidden gems to share? Feel free to open a pull request or an issue!

---

## 🧑‍💻 Author

Created by [Rahmatulloh Kholmatov](https://github.com/kholmatov.dev)
Flutter Developer & Open Source Enthusiast 🚀

---

## ⭐️ Star the repo

If you found this repo helpful, don't forget to **star** it!
