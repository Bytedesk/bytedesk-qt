# ByteDesk Qt Client

> A cross-platform instant messaging client based on C++ + Qt + MQTT

[![Qt](https://img.shields.io/badge/Qt-6.10%2B-41CD52?logo=qt)](https://www.qt.io)
[![C++](https://img.shields.io/badge/C++-17-00599C?logo=c%2B%2B)](https://en.cppreference.com/w/C++17)
[![License](https://img.shields.io/badge/License-BSL--1.1-blue)](LICENSE)

**Language:** [English](README.md) | [中文](README.zh.md)

---

## ✨ Features

- ✅ **User Authentication** - Login/logout, automatic token refresh
- ✅ **Real-time Communication** - MQTT persistent connection, instant message delivery
- ✅ **Thread Management** - Load, switch, and refresh thread lists
- ✅ **Messaging** - Real-time text message sending and receiving
- ✅ **Cross-platform** - Supports Windows, macOS, and Linux
- ✅ **Lightweight** - Pure Qt implementation, no third-party MQTT library dependencies

---

## 🚀 Quick Start

### Build and Run

```bash
# Method 1: Qt Creator (Recommended)
1. Open bytedesk.pro
2. Click the Run button (or press Ctrl+R)

# Method 2: Command Line
qmake bytedesk.pro && make
./qt

# Method 3: Build Script
./build.sh
```

### Using Qt Creator (Recommended)

Qt Creator provides the best development experience with syntax highlighting, code completion, and integrated debugging.

#### Step 1: Install Qt Creator

1. Download Qt Creator from [qt.io](https://www.qt.io/download)
2. Install Qt 6.10 or later
3. Make sure to include these components:
   - Qt Creator IDE
   - Qt 6.x (Desktop compilers)
   - CMake/qmake build tools

#### Step 2: Open Project

1. Launch Qt Creator
2. Click **File → Open File or Project** (or press Ctrl+O)
3. Navigate to the project directory
4. Select `bytedesk.pro` file
5. Click **Open**

#### Step 3: Configure Build Kit

On the **Configure Project** screen:

1. **Select Kit**: Choose the appropriate Qt Kit for your platform
   - **Desktop Qt 6.10.x clang 64bit** (macOS)
   - **Desktop Qt 6.10.x MinGW 64-bit** (Windows)
   - **Desktop Qt 6.10.x GCC 64bit** (Linux)

2. **Configure Settings** (if needed):
   - Click **Projects** button on left sidebar
   - Select **Build & Run**
   - Verify build directory: `../build-bytedesk-Desktop_Qt_6-Debug`
   - Adjust if necessary

3. Click **Configure Project**

#### Step 4: Build the Project

1. Click the **Build** icon (hammer) in bottom-left corner (or press Ctrl+B)
2. Watch the **Compile Output** panel at the bottom
3. Wait for build to complete (should show "Elapsed time: xx:xx")

**Build Status:**
- ✅ Green checkmark: Build successful
- ❌ Red X: Build failed (check errors in Compile Output)

#### Step 5: Run the Application

1. Click the **Run** button (green play icon) or press **Ctrl+R**
2. The application window will appear
3. Check the **Application Output** panel for runtime logs

#### Qt Creator Tips

**Keyboard Shortcuts:**
- `Ctrl+B` - Build project
- `Ctrl+R` - Run application
- `Ctrl+.` - Follow symbol under cursor
- `F2` - Jump to definition
- `Shift+F2` - Switch between header and source
- `Ctrl+K` - Search in file
- `Ctrl+Shift+F` - Search in all files
- `Ctrl+L` - Go to line
- `Ctrl+/` - Comment/uncomment selection

**Useful Features:**
- **Auto-completion**: Press `Tab` or `Ctrl+Space` while typing
- **Code Navigation**: Hold `Ctrl` + click on function/class to jump
- **Split View**: Right-click tab → **Open in New Split**
- **Bookmarks**: Right-click line number → **Toggle Bookmark**
- **Tasks**: `// TODO: fix this` appears in Tasks panel

**Debugging:**
1. Click **Debug** button (bug icon) or press **F5**
2. Set breakpoints by clicking line number (red dot appears)
3. Use debug controls:
   - **F10** - Step over
   - **F11** - Step into
   - **Shift+F11** - Step out
   - **F5** - Continue

#### Troubleshooting Qt Creator

**Problem: "No valid Kit found"**
- Solution: Open **Tools → Options → Kits**
- Add Qt version: **Qt Versions → Add** → Select qmake
- Add compiler: **Compilers → Add** → Auto-detected or manual
- Create Kit: **Kits → Add** → Select Qt version and compiler

**Problem: Build errors but no output**
- Solution: Click **Window → Output Panes → Compile Output**
- Check **General → Messages** for warnings

**Problem: Cannot run application**
- Solution: Go to **Projects → Run**
- Check **Executable** field points to correct binary
- **Run → Environment** - add needed variables if required

**Problem: Code completion not working**
- Solution: **Tools → Options → C++ → Code Model**
- Click **Reset Code Model**
- Restart Qt Creator

### System Requirements

- **Qt 6.10+**
- **C++17** compiler
- **macOS**: 10.15+ (Catalina)
- **Windows**: 10+
- **Linux**: GCC 7+ or Clang 6+

---

## 📱 User Guide

### 1. Launch Application

When you run the program, you will see the main window:

```
┌──────────────────────────────────────────┐
│ Weiyu - ByteDesk Qt Client              │
├──────────────────────────────────────────┤
│ Menu: [Login] [Logout] [Refresh] [Exit] │
├──────────────┬───────────────────────────┤
│ Thread List  │ Chat Window               │
│              │                            │
│ ☐ Thread 1  │ [10:30] Zhang San: Hi!    │
│ ☐ Thread 2  │ [10:31] Me: Hello!        │
│ ☐ Thread 3  │                            │
│              │ [Type message.....] [Send]│
├──────────────┴───────────────────────────┤
│ Status: Welcome to ByteDesk Qt - Please login│
└──────────────────────────────────────────┘
```

### 2. Login

1. Click menu **"Menu" → "Login"**
2. Enter username and password
3. Click OK

### 3. Send Message

1. Click on a thread in the left thread list to select it
2. Type your message in the input box
3. Click "Send" or press Enter

### 4. Receive Messages

- New messages will appear in real-time in the chat window
- Your messages are displayed in blue
- Others' messages are displayed in green

---

## 🏗️ Project Structure

```
qt/
├── bytedesk.pro              # qmake project file
├── build.sh                  # Build script
├── verify.sh                 # Verification script
└── src/
    ├── main.cpp              # Program entry point
    │
    ├── models/               # Data models (8 files)
    │   ├── message.cpp/h     # Message model
    │   ├── thread.cpp/h      # Thread model
    │   ├── user.cpp/h        # User model
    │   └── config.cpp/h      # Configuration model
    │
    ├── core/                 # Core functionality (14 files)
    │   ├── auth/            # Authentication management
    │   │   └── authmanager.cpp/h
    │   ├── mqtt/            # MQTT communication (TCP implementation)
    │   │   ├── mqttclient.cpp/h
    │   │   └── mqttmessagehandler.cpp/h
    │   └── network/         # HTTP API
    │       ├── httpclient.cpp/h
    │       ├── apibase.cpp/h
    │       ├── authapi.cpp/h
    │       ├── messageapi.cpp/h
    │       └── threadapi.cpp/h
    │
    └── ui/                   # User interface (3 files)
        ├── mainwindow.cpp/h  # Main window
        └── mainwindow.ui     # UI design
```

---

## 💡 Code Examples

### Initialize Components

```cpp
#include "models/config.h"
#include "core/network/httpclient.h"
#include "core/network/authapi.h"
#include "core/mqtt/mqttclient.h"
#include "core/auth/authmanager.h"

// Configure server
BYTDESK_CONFIG->setApiUrl("https://api.bytedesk.com");

// Create HTTP client
HttpClient* httpClient = new HttpClient(this);
httpClient->setBaseUrl(BYTDESK_CONFIG->getApiUrl());

// Create authentication manager
AuthApi* authApi = new AuthApi(httpClient, this);
MqttClient* mqttClient = new MqttClient(this);
AuthManager* authManager = new AuthManager(authApi, mqttClient, this);
```

### Login

```cpp
// Connect signals
connect(authManager, &AuthManager::loginSuccess, [](const UserPtr& user) {
    qDebug() << "Login successful:" << user->getUsername();
});

// Execute login
authManager->login("username", "password");
```

### Send Message

```cpp
#include "core/mqtt/mqttmessagehandler.h"

MqttMessageHandler* mqttHandler = new MqttMessageHandler(mqttClient, this);
mqttHandler->init();

// Send text message
mqttHandler->sendTextMessage(thread, "Hello, World!", currentUser);

// Receive messages
connect(mqttHandler, &MqttMessageHandler::messageReceived,
        [](const MessagePtr& msg) {
    qDebug() << "Message received:" << msg->getContentString();
});
```

---

## 🛠️ Tech Stack

### Core Technologies

- **Qt 6.10+** - Cross-platform UI framework
- **C++17** - Modern C++ standard
- **MQTT 3.1.1** - Real-time messaging protocol (TCP implementation)
- **HTTP/HTTPS** - REST API calls

### Qt Modules

- `QtCore` - Core functionality
- `QtGui` - GUI foundation
- `QtWidgets` - UI components
- `QtNetwork` - Network communication
- `QtSql` - Database (to be integrated)

---

## 🔧 Configuration

### Change Server Address

Edit `src/models/config.cpp`:

```cpp
const QString Config::DEFAULT_API_URL = "https://your-server.com";
const QString Config::DEFAULT_MQTT_HOST = "mqtt.your-server.com";
const int Config::DEFAULT_MQTT_PORT = 1883;
```

### Configuration File Location

Application configuration is saved to:

- **macOS**: `~/Library/Preferences/com.bytedesk.qt.plist`
- **Linux**: `~/.config/Bytedesk/bytedesk-qt.conf`
- **Windows**: `%APPDATA%/Bytedesk/bytedesk-qt.conf`

---

## 🎯 Feature Status

### Implemented ✅

- [x] User login/logout
- [x] Automatic token refresh
- [x] Thread list management
- [x] Text message sending/receiving
- [x] MQTT real-time communication
- [x] HTTP API wrapper
- [x] Persistent configuration
- [x] Complete UI interface

### Under Development ⚠️

- [ ] File upload/download
- [ ] Image message preview
- [ ] Historical message loading
- [ ] Message recall
- [x] Unread message count
- [ ] SQLite database
- [ ] Emoji support
- [ ] Search functionality

---

## 🐛 FAQ

### 1. Compilation Error: Qt Module Not Found

**Solution**:
- Qt Creator: Check Kit configuration
- Command line: Set correct Qt path
```bash
export PATH=$PATH:~/Qt/6.10.1/macos/bin
```

### 2. MQTT Connection Failed

**Solution**:
- Check server address and port
- Confirm network connection
- Verify token is valid
- Check console logs

### 3. Login Failed

**Solution**:
- Confirm server address is correct
- Check username and password
- Check status bar error message

### 4. Message Send Failed

**Solution**:
- Ensure you are logged in
- Ensure a thread is selected
- Check MQTT connection status

---

## 📊 Project Completion

| Module | Completion | Files |
|------|------------|-------|
| Data Models | ✅ 100% | 8 |
| Core Features | ✅ 100% | 14 |
| UI Interface | ✅ 80% | 3 |
| Documentation | ✅ 100% | - |
| **Total** | **✅ 95%** | **25** |

---

## 🔗 Related Resources

- **Desktop Version**: [ByteDesk Desktop](../../frontend/apps/desktop) - Electron + React version
- **Backend API**: [ByteDesk Backend](../../starter) - Java Spring Boot
- **Website**: https://www.bytedesk.com
- **Documentation**: https://docs.bytedesk.com

---

## 📄 License

Business Source License 1.1

Free for internal use and development. Prohibited:
- Resale or SaaS hosting
- Deployment for illegal business
- Unauthorized commercial distribution

---

## 🤝 Contributing

Issues and Pull Requests are welcome!

---

<div align="center">

**Made with ❤️ by ByteDesk**

[Website](https://www.bytedesk.com) • [Documentation](https://docs.bytedesk.com) • [GitHub](https://github.com/bytedesk)

</div>
