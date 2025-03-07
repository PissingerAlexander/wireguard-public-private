# wireguard-public-private
Wireguard for a public server and a private peer, to route all traffic from the public server to the private client

# Setup
## Wireguard on server and peer
1. Install `wireguard` on both servers.
2. Generate public and private key on both servers (`wg genkey | tee privateKey | wg pubkey > publicKey`).
3. Create configuration on both servers wg0.conf (in this repo `wireguard.conf.d/server.wg0.conf` for the server and `wireguard.conf.d/peer.wg0.conf` for the peer).
4. Enable packet forwarding: edit `/etc/sysctl.conf` and uncomment or add `net.ipv4.ip_forward = 1`, then run `sudo sysctl -p` to apply changes.
5. Open all needed ports in the firewall (on the peer, on the router, on the server, maybe on the server provider website).
6. Start wireguard and test (maybe first on the server then on the peer).

## Traffic forwarding via nginx
1. Install `Nginx` on both servers (if neede with the stream module).
2. Create nginx configuration (an example in this repo is `nginx.conf.d/server.default.conf`for the server and `nginx.conf.d/peer.default.conf` for the peer).
3. Start Nginx on both servers and test.
