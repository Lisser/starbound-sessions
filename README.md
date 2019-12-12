# Setting up the server
1. Spin up Ubuntu server (including SSH public keys)
2. Move starbound zip:
    * The starbound binary is currently not yet centrally hosted, but it's on my Macbook
    * Push binary to server with:
    * `scp -r ~/downloads/starbound_1.4.4_linux.zip root@<ip-address>:~/`
3. Unpack
    * `apt-get install unzip`
    * `unzip starbound_1.4.4_linux.zip -d starbound`
4. Clone universe & mods `git clone https://github.com/Lisser/starbound-sessions.git`
5. Extract universe `rsync -r ~/starbound-sessions/storage/universe ~/starbound/starbound_1.4.4_linux/storage/`
6. Extract mods `rsync -r ~/starbound-sessions/mods ~/starbound/starbound_1.4.4_linux`
7. Open firewall `ufw allow 21025`
8. Start server:
    * `screen -S starbound`
    * `cd ~/starbound/starbound_1.4.4_linux/linux/`
    * `chmod +x starbound_server`
    * `./starbound_server`
9. Detach
    * `ctrl a`
    * `d`
10. Attach
    * `screen -r starbound`

# Spinning down 
1. Copy universe and config to repo
    * `cp -R ~/starbound/starbound_1.4.4_linux/storage/universe ~/starbound-sessions/storage`
    * `cp ~/starbound/starbound_1.4.4_linux/storage/starbound_server.config ~/starbound-sessions/storage`