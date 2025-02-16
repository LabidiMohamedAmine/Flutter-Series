import 'package:flutter/material.dart';
import 'package:avatar_glow/avatar_glow.dart';

void main() {
  runApp(MaterialApp(
    home: FirstScreen(),
    debugShowCheckedModeBanner: false,
  ));
}

// First Screen (Initial Small Avatar)
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.blueGrey[900],
      appBar: AppBar(
        foregroundColor: Colors.white,
        title: Text(
          "Hero + Glow Effect",
          style: TextStyle(fontWeight: FontWeight.bold, fontSize: 30),
        ),
        backgroundColor: Colors.transparent,
      ),
      body: Center(
        child: GestureDetector(
          onTap: () {
            Navigator.push(
              context,
              PageRouteBuilder(
                pageBuilder: (context, animation, secondaryAnimation) =>
                    SecondScreen(),
                transitionsBuilder:
                    (context, animation, secondaryAnimation, child) {
                  return FadeTransition(opacity: animation, child: child);
                },
              ),
            );
          },
          child: AvatarGlow(
            glowColor: Colors.blue,
            duration: const Duration(milliseconds: 2000),
            repeat: true,
            animate: true,
            child: Hero(
              tag: 'heroTag',
              child: Material(
                color: Colors.transparent,
                child: Container(
                  width: 120,
                  height: 120,
                  decoration: BoxDecoration(
                    gradient: LinearGradient(
                      colors: [Colors.blue, Colors.lightBlueAccent],
                      begin: Alignment.topLeft,
                      end: Alignment.bottomRight,
                    ),
                    borderRadius: BorderRadius.circular(20),
                    boxShadow: [
                      BoxShadow(
                        color: Colors.blue.withOpacity(0.5),
                        blurRadius: 10,
                        spreadRadius: 2,
                        offset: Offset(2, 4),
                      )
                    ],
                  ),
                  child: Center(
                    child: Icon(Icons.image, size: 50, color: Colors.white),
                  ),
                ),
              ),
            ),
          ),
        ),
      ),
    );
  }
}

// Second Screen (Expanded Avatar)
class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.blueGrey[900],
      body: Center(
        child: GestureDetector(
          onTap: () {
            Navigator.pop(context); // Navigate back to the first screen
          },
          child: Hero(
            tag: 'heroTag',
            child: Material(
              color: Colors.transparent,
              child: Container(
                width: MediaQuery.of(context).size.width * 0.8,
                height: MediaQuery.of(context).size.width * 0.8,
                decoration: BoxDecoration(
                  gradient: LinearGradient(
                    colors: [Colors.blue, Colors.lightBlueAccent],
                    begin: Alignment.topLeft,
                    end: Alignment.bottomRight,
                  ),
                  borderRadius: BorderRadius.circular(40),
                  boxShadow: [
                    BoxShadow(
                      color: Colors.blue.withOpacity(0.5),
                      blurRadius: 20,
                      spreadRadius: 4,
                      offset: Offset(4, 6),
                    )
                  ],
                ),
                child: Center(
                  child: Icon(Icons.image, size: 100, color: Colors.white),
                ),
              ),
            ),
          ),
        ),
      ),
    );
  }
}
