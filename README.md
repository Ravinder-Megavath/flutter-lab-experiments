# Flutter Lab Experiments

This repository contains a collection of Flutter & Dart experiments for learning the basics of mobile app development using **Dart**, **Widgets**, **Layouts**, **Responsive UI**, **Navigation**, and **State Management**.

---

## 📌 Experiment 1: Dart Basics

### a) Simple Dart Program
```dart
void main() {
  print("Hello Flutter!");
  int x = 5, y = 7;
  print("Sum = ${x + y}");
}
b) Install Flutter/Dart
Installation steps for environment setup (no code required).
👉 Follow instructions from flutter.dev to install Flutter and Dart.

📌 Experiment 2: Widgets & Layouts
a) Basic Widgets (Text, Image, Container)
dart
import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(home: Scaffold(
  appBar: AppBar(title: const Text("Widgets")),
  body: Column(children: [
    const Text("Hello Flutter!"),
    Image.network("https://flutter.dev/images/flutter-logo-sharing.png", width: 80),
    Container(color: Colors.blue, padding: const EdgeInsets.all(8),
      child: const Text("Container Text", style: TextStyle(color: Colors.white))),
  ]),
)));
b) Layouts (Row, Column, Stack)
dart
import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(home: Scaffold(
  appBar: AppBar(title: const Text("Layouts")),
  body: Column(children: [
    Row(mainAxisAlignment: MainAxisAlignment.spaceEvenly, children: const [
      Icon(Icons.home), Icon(Icons.star), Icon(Icons.settings),
    ]),
    SizedBox(height: 20),
    Stack(children: [
      Container(width: 150, height: 150, color: Colors.orange),
      Positioned(top: 40, left: 40, child: Container(width: 70, height: 70, color: Colors.purple)),
    ])
  ]),
)));
📌 Experiment 3: Responsive UI
a) Using MediaQuery
dart
import 'package:flutter/material.dart';

void main() => runApp(const MaterialApp(home: ResponsiveApp()));

class ResponsiveApp extends StatelessWidget {
  const ResponsiveApp({super.key});
  @override
  Widget build(BuildContext context) {
    double w = MediaQuery.of(context).size.width;
    return Scaffold(body: Center(
      child: Text(w < 600 ? "Mobile" : w < 1200 ? "Tablet" : "Desktop"),
    ));
  }
}
b) Using LayoutBuilder
dart
import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(home: Scaffold(
  body: LayoutBuilder(builder: (ctx, c) {
    if (c.maxWidth < 600) return const Text("Mobile View");
    if (c.maxWidth < 1200) return const Text("Tablet View");
    return const Text("Desktop View");
  }),
)));
📌 Experiment 4: Navigation
a) Push & Pop
dart
import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(home: First()));

class First extends StatelessWidget {
  @override
  Widget build(BuildContext c) => Scaffold(
    appBar: AppBar(title: const Text("First")),
    body: Center(child: ElevatedButton(
      onPressed: () => Navigator.push(c, MaterialPageRoute(builder: (_) => Second())),
      child: const Text("Go Next"),
    )),
  );
}

class Second extends StatelessWidget {
  @override
  Widget build(BuildContext c) => Scaffold(
    appBar: AppBar(title: const Text("Second")),
    body: Center(child: ElevatedButton(
      onPressed: () => Navigator.pop(c), child: const Text("Back")),
    ),
  );
}
b) Named Routes
dart
import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(
  initialRoute: '/', routes: {
    '/': (_) => const Home(),
    '/second': (_) => const Second(),
  },
));

class Home extends StatelessWidget {
  const Home({super.key});
  @override
  Widget build(BuildContext c) => Scaffold(
    appBar: AppBar(title: const Text("Home")),
    body: Center(child: ElevatedButton(
      onPressed: () => Navigator.pushNamed(c, '/second'),
      child: const Text("Go Second"),
    )),
  );
}

class Second extends StatelessWidget {
  const Second({super.key});
  @override
  Widget build(BuildContext c) => Scaffold(
    appBar: AppBar(title: const Text("Second")),
    body: Center(child: ElevatedButton(
      onPressed: () => Navigator.pop(c), child: const Text("Back")),
    ),
  );
}
📌 Experiment 5: Stateful vs Stateless
a) Stateless Example
dart
import 'package:flutter/material.dart';

void main() => runApp(const MaterialApp(home: Text("I am Stateless")));
b) Stateful Counter
dart
import 'package:flutter/material.dart';

void main() => runApp(const MaterialApp(home: Counter()));

class Counter extends StatefulWidget {
  const Counter({super.key});
  @override State<Counter> createState() => _CounterState();
}

class _CounterState extends State<Counter> {
  int count = 0;
  @override
  Widget build(BuildContext c) => Scaffold(
    appBar: AppBar(title: const Text("Counter")),
    body: Center(child: Column(mainAxisAlignment: MainAxisAlignment.center, children: [
      Text("Count: $count"),
      ElevatedButton(onPressed: () => setState(() => count++), child: const Text("Add")),
    ])),
  );
}
🚀 How to Run
Install Flutter & Dart → Setup Guide

Clone this repo:

bash
git clone https://github.com/Ravinder-Megavath/flutter-lab-experiments.git
cd flutter-lab-experiments
Run any experiment:

bash
flutter run
