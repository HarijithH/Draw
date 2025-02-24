# Draw
import 'package:flutter/material.dart';


class draw extends StatelessWidget {
  const draw({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: const HomeScreen(),
    );
  }
}

class HomeScreen extends StatefulWidget {
  const HomeScreen({super.key});

  @override
  _HomeScreenState createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {
  String _content = 'Home Page';
  List<String> _itemList = ['good', 'nice', 'poor'];

  void _updateContent(String newContent) {
    setState(() {
      _content = newContent;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Drawer Example"),
        backgroundColor: Colors.brown,
      ),
      drawer: Drawer(
        child: ListView(
          children: <Widget>[
            Expanded(
              child: DrawerHeader(
                margin: EdgeInsets.zero,
                padding: EdgeInsets.zero,
                decoration: const BoxDecoration(color: Colors.blue),
                child: SizedBox(
                  height: 300,
                  child: Stack(
                    children: [
                      Align(
                        alignment: Alignment.topRight,
                        child: Padding(
                          padding: EdgeInsets.all(10), // Add some padding for better spacing
                          child: Icon(Icons.settings, color: Colors.white,size: 24,), // Settings icon
                        ),
                      ),
                      Column(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          const CircleAvatar(
                            radius: 30.0,
                            backgroundImage: AssetImage('assets/images/ge.jpg'),
                          ),
                          const SizedBox(height: 10),
                          const Text(
                            'Harijith P',
                            style: TextStyle(
                              color: Colors.white,
                              fontSize: 20,
                              fontWeight: FontWeight.bold,
                            ),
                          ),
                          const SizedBox(height: 10),
                          const Text(
                            'Software Developer',
                            style: TextStyle(
                              color: Colors.white,
                              fontSize: 14,
                              fontWeight: FontWeight.w300,
                            ),
                          ),
                          const SizedBox(height: 10),
                          Row(
                            mainAxisAlignment: MainAxisAlignment.center,
                            children: const [
                              Icon(Icons.favorite, color: Colors.white, size: 24),
                              SizedBox(width: 20),
                              Icon(Icons.grid_view, color: Colors.white, size: 24),
                            ],
                          ),
                        ],
                      ),
                    ],
                  ),
                ),
              ),
            ),


            ListTile(
              leading: const Icon(Icons.feed),
              title: const Text('Feed'),
              onTap: () {
                _updateContent('Feed');
                Navigator.pop(context);
              },
            ),
            ListTile(
              leading: const Icon(Icons.event),
              title: const Text('Events'),
              onTap: () {
                _updateContent('Events');
                Navigator.pop(context);
              },
            ),
            ListTile(
              leading: const Icon(Icons.camera),
              title: const Text('Post'),
              onTap: () {
                _updateContent('Post');
                Navigator.pop(context);
              },
            ),
            ListTile(
              leading: const Icon(Icons.notifications), // Notification icon
              title: const Text('Notifications'),
              trailing: Container(
                padding: const EdgeInsets.all(6),
                decoration: BoxDecoration(
                  color: Colors.blue, // Badge color
                  borderRadius: BorderRadius.circular(10),
                ),
                constraints: const BoxConstraints(
                  minWidth: 24,
                  minHeight: 20,
                ),
                child: const Text(
                  '3', // Notification count
                  style: TextStyle(
                    color: Colors.white,
                    fontSize: 12,
                    fontWeight: FontWeight.bold,
                  ),
                  textAlign: TextAlign.center,
                ),
              ),
              onTap: () {
                _updateContent('Notification');
                Navigator.pop(context);
              },
            ),


            ListTile(
              leading: const Icon(Icons.person),
              title: const Text('Account'),
              onTap: () {
                _updateContent('Account');
                Navigator.pop(context);
              },
            ),
            ListTile(
              leading: const Icon(Icons.logout),
              title: const Text('Logout'),
              onTap: () {
                _updateContent('Logout');
                Navigator.pop(context);
              },
            ),
          ],
        ),
      ),
      body: _buildBody(),
    );
  }

  Widget _buildBody() {
    if (_content == 'Feed') {
      return ListView.builder(
        itemCount: _itemList.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(_itemList[index]),
          );
        },
      );
    } else if (_content == 'Events') {
      return Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: const [
            Icon(Icons.sports_football, size: 50),
            SizedBox(height: 10),
            Text('Football', style: TextStyle(fontSize: 18)),
          ],
        ),
      );
    }
    else if (_content == 'Post') {
      return Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: const [
            Icon(Icons.collections, size: 50),
            SizedBox(height: 10),
            Text('Albums', style: TextStyle(fontSize: 18)),
          ],
        ),
      );
    }
    else if (_content == 'Notification') {
      return Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: const [
            Icon(Icons.notification_add, size: 50),
            SizedBox(height: 10),
            Text('Notification', style: TextStyle(fontSize: 18)),
          ],
        ),
      );
    }
    else if (_content == 'Account') {
      return Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: const [
            Icon(Icons.info, size: 50),
            SizedBox(height: 10),
            Text('Informaion', style: TextStyle(fontSize: 18)),
          ],
        ),
      );
    }
    return Center(
      child: Text(
        _content,
        style: const TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
      ),
    );
  }
}


