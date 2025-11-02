# Python Chat Application

A real-time multi-client chat application built with Python sockets and Tkinter GUI. The application consists of a server that manages multiple client connections and a client interface for sending and receiving messages.

## Features

- Real-time messaging between multiple clients
- User-friendly GUI built with Tkinter
- Multi-threaded server to handle multiple simultaneous connections
- Username-based identification
- Broadcast messaging to all connected users
- Connection status notifications
- Modern dark-themed UI with ocean blue accents
- Keyboard shortcuts (Enter key to send messages and join)

## Components

### Server (`server.py`)
- Manages multiple client connections (configurable limit)
- Broadcasts messages to all connected users
- Thread-based client handling for concurrent connections
- Active client tracking
- Real-time connection notifications

### Client (`client.py`)
- Clean, intuitive GUI interface
- Scrollable message display area
- Username registration
- Real-time message sending and receiving
- Copy-paste functionality
- Error handling with popup notifications

## Requirements

- Python 3.x
- tkinter (usually comes pre-installed with Python)
- socket (standard library)
- threading (standard library)

## Installation

1. Clone this repository or download the files
2. Ensure Python 3.x is installed on your system
3. No additional packages required - uses Python standard library

## Configuration

Before running, configure the network settings:

### In `server.py`:

`HOST = '127.0.0.1' # Server IP address
PORT = 1234 # Port number (0-65535)
LISTENER_LIMIT = 2 # Maximum concurrent connections`


### In `client.py`:

`HOST = '192.168.151.36' # Server IP address
PORT = 1234 # Port number (must match server)`


**Note**: Change `HOST` to match your server's IP address. Use `'127.0.0.1'` for localhost testing.

## Usage

### Starting the Server

1. Run the server script:
`python server.py`


2. The server will start listening for connections:
`Running the server on 127.0.0.1 1234`


### Starting the Client

1. Run the client script:
`python client.py`


2. Enter your username in the text field
3. Click "Join" or press Enter to connect
4. Start chatting!

### Sending Messages

- Type your message in the bottom text box
- Click "Send" or press Enter
- Your message will be broadcast to all connected users

## User Interface

### Color Scheme
- **Background**: Dark Grey (#121212)
- **Secondary Background**: Medium Grey (#1F1B24)
- **Accent**: Ocean Blue (#464EB8)
- **Text**: White

### Layout
- **Top Frame**: Username input and join button
- **Middle Frame**: Scrollable message display area (600x400px)
- **Bottom Frame**: Message input and send button

## Features Breakdown

### Server Features
- Multi-threaded architecture for handling multiple clients
- Real-time message broadcasting
- Client connection/disconnection notifications
- Active user tracking
- Error handling for empty messages

### Client Features
- Thread-based message listening
- Automatic message display
- Connection status feedback
- Input validation (non-empty username and messages)
- Keyboard shortcuts for quick interaction
- Disabled controls after connection to prevent changes

## Error Handling

The application handles various error scenarios:
- Empty username validation
- Empty message validation
- Connection failures
- Server unavailability
- Invalid network configurations
- Empty message reception

## Network Requirements

- Both server and client must be on the same network (or use port forwarding)
- Firewall must allow connections on the specified port
- For internet-based connections, configure router port forwarding

## Limitations

- Maximum concurrent users: Configurable via `LISTENER_LIMIT`
- Message buffer: 2048 bytes per message
- No message persistence (messages are not saved)
- No private messaging support
- No encryption (messages sent in plain text)

## Future Enhancements

Potential improvements:
- Private messaging between users
- Message encryption
- User authentication
- Message history persistence
- File sharing capabilities
- Emoji support
- User typing indicators
- Online user list display

## Troubleshooting

### "Unable to connect to server" Error
- Verify server is running
- Check HOST and PORT match between client and server
- Ensure firewall allows the connection
- Verify network connectivity

### "Unable to bind to host" Error
- Port may already be in use
- Try a different port number
- Check if another instance is running

### Connection Drops
- Check network stability
- Verify server is still running
- Check for firewall interruptions

## License

This project is open source and available for personal and educational use.

## Technical Details

### Socket Configuration
- **Protocol**: TCP (SOCK_STREAM)
- **Address Family**: IPv4 (AF_INET)
- **Buffer Size**: 2048 bytes
- **Architecture**: Client-Server with multi-threading

### Threading Model
- Server: One thread per connected client
- Client: Separate thread for listening to incoming messages
- Main thread: Handles GUI events and user interactions
