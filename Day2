import 'package:flutter/material.dart';

void main() {
  WidgetsFlutterBinding.ensureInitialized();
  runApp(const MagicLoaderApp());
}

class MagicLoaderApp extends StatelessWidget {
  const MagicLoaderApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Future Tech Loader',
      debugShowCheckedModeBanner: false,
      theme: ThemeData.dark().copyWith(
        scaffoldBackgroundColor: Colors.black,
      ),
      home: const Scaffold(
        body: SafeArea(
          child: TechLoaderScreen(),
        ),
      ),
    );
  }
}

class TechLoaderScreen extends StatefulWidget {
  const TechLoaderScreen({super.key});

  @override
  State<TechLoaderScreen> createState() => _TechLoaderScreenState();
}

class _TechLoaderScreenState extends State<TechLoaderScreen>
    with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  double _progress = 0.0;
  final List<Color> _neonColors = [
    const Color(0xFF00F7FF),
    const Color(0xFFAD00FF),
    const Color(0xFFFF0077),
  ];

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(
      vsync: this,
      duration: const Duration(milliseconds: 1500),
    )
      ..addListener(_safeProgressUpdate)
      ..repeat(reverse: true);
  }

  void _safeProgressUpdate() {
    final clampedValue = _controller.value.clamp(0.0, 1.0);
    setState(() {
      _progress = (clampedValue * 100).clamp(0, 100);
    });
  }

  @override
  void dispose() {
    _controller
      ..stop()
      ..dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        const Padding(
          padding: EdgeInsets.all(20.0),
          child: Text(
            'Initializing Future Tech',
            style: TextStyle(
              fontSize: 28,
              fontWeight: FontWeight.w300,
              color: Colors.white54,
              letterSpacing: 2.0,
            ),
          ),
        ),
        _buildSafeHoloGrid(),
        const SizedBox(height: 40),
        _buildValidatedLoaderAnimation(),
        const SizedBox(height: 40),
        _buildProgressText(),
        const SizedBox(height: 20),
        _buildTechLabels(),
      ],
    );
  }

  Widget _buildValidatedLoaderAnimation() {
    return AnimatedBuilder(
      animation: _controller,
      builder: (context, child) {
        final safeValue = _controller.value.clamp(0.0, 1.0);
        return Row(
          mainAxisAlignment: MainAxisAlignment.center,
          children: List.generate(3, (index) {
            final animation = CurvedAnimation(
              parent: _controller,
              curve: Interval(
                index * 0.2,
                1.0,
                curve: Curves.easeInOutBack,
              ),
            );

            return Stack(
              alignment: Alignment.center,
              children: [
                AnimatedContainer(
                  duration: const Duration(milliseconds: 200),
                  width: 60,
                  height: 60,
                  decoration: BoxDecoration(
                    shape: BoxShape.circle,
                    boxShadow: [
                      BoxShadow(
                        color: _neonColors[index].withOpacity(
                            (animation.value.clamp(0.0, 1.0) * 0.5)),
                        blurRadius: 20,
                        spreadRadius: 5,
                      )
                    ],
                  ),
                ),
                Padding(
                  padding: const EdgeInsets.symmetric(horizontal: 15.0),
                  child: Transform(
                    transform: Matrix4.identity()
                      ..translate(0.0, -(animation.value.clamp(0.0, 1.0) * 40))
                      ..rotateZ(animation.value.clamp(0.0, 1.0) * 0.5),
                    child: Container(
                      width: 40,
                      height: 40,
                      decoration: BoxDecoration(
                        color: _neonColors[index],
                        borderRadius: BorderRadius.circular(8),
                        border: Border.all(
                          color: Colors.white.withOpacity(0.3),
                          width: 2,
                        ),
                      ),
                      child: const Icon(Icons.bolt, color: Colors.white),
                    ),
                  ),
                ),
              ],
            );
          }),
        );
      },
    );
  }

  Widget _buildProgressText() {
    return Column(
      children: [
        Text(
          '${_progress.toStringAsFixed(1)}%',
          style: TextStyle(
            fontSize: 36,
            fontWeight: FontWeight.bold,
            color: _neonColors[1],
            shadows: [
              Shadow(
                color: _neonColors[1].withOpacity(0.5),
                blurRadius: 10,
              )
            ],
          ),
        ),
        const SizedBox(height: 10),
        const Text(
          'Downloading AI modules...',
          style: TextStyle(color: Colors.white54),
        ),
      ],
    );
  }

  Widget _buildTechLabels() {
    return Wrap(
      spacing: 20,
      runSpacing: 10,
      children: const [
        TechLabel('Neural Networks'),
        TechLabel('Quantum Compute'),
        TechLabel('Blockchain AI'),
        TechLabel('IoT Matrix'),
      ],
    );
  }

  Widget _buildSafeHoloGrid() {
    return Container(
      height: 150,
      decoration: const BoxDecoration(
        gradient: LinearGradient(
          begin: Alignment.topCenter,
          end: Alignment.bottomCenter,
          colors: [
            Color(0x80000000), // Semi-transparent black
            Color(0x1A000000), // More transparent
          ],
        ),
      ),
    );
  }
}

class TechLabel extends StatelessWidget {
  final String text;

  const TechLabel(this.text, {super.key});

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.symmetric(horizontal: 15, vertical: 8),
      decoration: BoxDecoration(
        border: Border.all(color: Colors.white24),
        borderRadius: BorderRadius.circular(20),
      ),
      child: Text(
        text,
        style: const TextStyle(
          color: Colors.white70,
          fontSize: 12,
          letterSpacing: 1.2,
        ),
      ),
    );
  }
}
