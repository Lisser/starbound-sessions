# Setting up the server
1. Spin up Ubuntu server (including SSH public keys)
2. Move starbound zip:
    * The starbound binary is currently not yet centrally hosted, but it's on my Macbook
    * Push binary to server with:
    * `scp -r ~/downloads/starbound_1.4.4_linux.zip root@<ip-address>:~/`
3. Unpack
    * `apt-get install bsdtar`
    * `mkdir starbound && bsdtar --strip-components=1 -C starbound -xvf starbound_1.4.4_linux.zip`
4. Load this repository on top of the unpacked zip
    * Move into the directory `cd starbound`
    * Initiate git `git init`
    * Add this repository as a remote `git remote add origin git@github.com:Lisser/starbound-sessions.git`
    * Make sure the remote is known `git fetch`
    * Merge this repository’s master into the newly initiated repo `git merge origin/master`
    * Set up the current local branch to be the remote master, so we can push changes back `git branch --set-upstream-to origin/master`
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
1. Inside the `starbound` directory, commit all changes and push to this repository:
    * `git add -A`
    * `git commit -m "chore(save): data from 2019-12-12"` (change the date!)
    * `git push`

Note that you must have push access to this repository to spin down!


## Todo: work this all out in a script, or Docker container or something! :)
