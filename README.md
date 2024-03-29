# zatacka-server
The server end of a networked [Zatacka](https://en.wikipedia.org/wiki/Achtung,_die_Kurve!) remake.
Written in java, consists of a TLS login server and TCP game server (currently set up to run on a single machine).

## Requirements
* Authentication: Project uses self-signed certificates; one must therefore be deployed together with the client
* SQLite: Project uses an SQLite database, JDBC driver is required

## Functionality
* **Java non-blocking I/O networking**: both the TLS login server and TCP game server use only one thread per server
* **Multi-threaded game logic design**: separate games are assigned to nodes. Every node is executed on its own thread, and handles game tick updates as well as client updates 
* **Security**: Client username and password are sent over TLS connection during login; game server authenticates client based on token generated by login server. Only salted password hashes are stored.


## TODO:
* Complete the server-side game-logic loop (handling player updates, performing collision detection)
* Polish matchmaking pipeline and lobby system
* Provide instructions for generating TLS certificate and keystore
* Complete client side work and make repository public

## Further Work
* Explore functionality of building on top of UDP protocol for game-server
* Implement matchmaking and save players' games
* Further optimise thick-line collision detection algorithm

## Related
The client side of this project is written in Unity; its github repository will soon be made public

## Credits
* [Server and Client implementation with SSLEngine](https://github.com/alkarn/sslengine.example) - Built on top of NioSslPeer which implemented the handshake protocol
* [PNet](https://github.com/PvdBerg1998/PNet) - Inspired the design pattern for message events

## License

MIT License
