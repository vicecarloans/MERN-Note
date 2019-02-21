## I. Buffer

1. **Binary Data**:
    + To store a piece of data, the computer needs to convert that data to binary.
    + *Character Encoding* : how encoding (UTF-8) of a character should be represented in binaries
    ```javascript
    const Buffer = require('buffer').Buffer;
    
    const buffer = new Buffer('Buffer', 'utf-8');
    
    bufferText = buffer.toString()
    
    console.log(bufferText)
    ```
    
## II. Networking

1. **net** Module:
    + *net.Server* class is used to create TCP or local server
    + *net.Socket* is abstraction of TCP or local socket
    
2. **HTTP**: 
    + Basis for data communication on the internet
    + Communication takes place over TCP/IP
    + *Costs*:
        + TCP Handshake when establish new connection
        + HTTP headers on every message
        + You may end up pushing around more HTTP headers than data
    + *Polling*:
        + allows server to send push notification request to client
    + *Long Polling*:
        + servers waits until it has data to send
        + each req/res creates and closes a connection
        + client has to wait to send new dat

## III. Web Sockets:
    
+ Allows two way communication over a single tcp socket with a remote host
+ Bi-directional: Client and server and send message at any time
+ Full duplex: Client and server can send update at the same time
+ Single long running connection with established context
+ *Handshake*: 
    + Client initiates connection
    + Server responds( accepts the upgrade)
    + both sides notified that socket is open
    + either side can send messages
    
## IV. Socket.IO

+ Real time application framework
+ Wrapper around Websockets (browser + Node.js)
+ Send events between client and server (Pub/Sub)
+ NOT a WebSocket implementation
+ Adds following metadata to each packet:
    + the *packet type*
    + the *namespace*
    + the *ackId* when a message acknowledgement is needed
+ WebSocket client will not be able to successfully connect to a Socket.IO server and Socket.IO client will not be able to connect to a WebSocket server

1. Features:
    + *Reliability*: connections can be established with proxies, firewalls
    + *Auto-reconnection*: unless instructed, a disconnected client will try to reconnect forever, until the server is available again
    + *Disconnection detection*: a heartbeat mechanism is implemented allowing both server and client to know when the other one is not responding anymore
    + *Binary support*
    + *Multiplexing support*: creates separate communication changes
    + *Room support*: create different channels called Rooms, that sockets can join and leave. You can then broadcast to any given room.
    
2. Server API:
    + New connected client
    ```javascript
    io.on('connection', callback(socket))
    ```
    + Socket:
    ```javascript
    socket.on(event, callback(data)) //attach new listener
    socket.emit(event, data) //send the event to this client
    socket.broadcast.emit(event,data) //send the event to all clients
    ```
    
3. Client API:
    ```javascript
    socket.on(event, callback(data))
    socket.emit(event, data)
    ```
    
4. Multiple Sockets:
    + Each new Client represents a new socket connection
    + We can define a socket to a namespace or a room
    ```javascript
    io.sockets.emit('hi', 'everyone')
    io.emit('hi', 'everyone');
    
    //Join to subscribe the socket to a given channel
    io.on('connection', function(socket){
        socket.join('room')
    })
    
    //Send a message to given room using to or in
    io.to('room').emit('some event')
    ```
    
    