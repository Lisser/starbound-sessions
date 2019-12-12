# Setting up the server
1. Spin up Ubuntu server (including SSH public keys)
2. Move starbound zip:
    * The starbound binary is currently not yet centrally hosted, but it's on my Macbook
    * Push binary to server with:
    * `scp -r ~/downloads/starbound_1.4.4_linux.zip root@<ip-address>:~/`
3. Unpack
    * `apt-get install unzip`
    * `unzip starbound_1.4.4_linux.zip -d starbound`
3. git clone https://github.com/Lisser/starbound-sessions.git