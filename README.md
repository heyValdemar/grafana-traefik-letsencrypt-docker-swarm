# Grafana with Let's Encrypt in a Docker Swarm

Install Docker Swarm by following my [guide](https://www.heyvaldemar.com/install-docker-swarm-on-ubuntu-server/).

Configure Traefik and create secrets for storing the passwords on the Docker Swarm manager node before applying the configuration.

Traefik [configuration](https://github.com/heyValdemar/traefik-letsencrypt-docker-swarm).

Create a secret for storing the password for Grafana database using the command:

`printf "YourPassword" | docker secret create grafana-postgres-password -`

Create a secret for storing the password for Grafana administrator using the command:

`printf "YourPassword" | docker secret create grafana-application-password -`

Create a secret for storing the password for Grafana email account using the command:

`printf "YourPassword" | docker secret create grafana-email-password -`

Clear passwords from bash history using the command:

`history -c && history -w`

Create a secret for storing the Grafana configuration using the command:

`docker secret create ldap.toml /path/to/ldap.toml`

Run `grafana-restore-application-data.sh` on the Docker Swarm worker node where the container for backups is running to restore application data if needed.

Run `docker stack ps grafana | grep grafana_backup | awk 'NR > 0 {print $4}'` on the Docker Swarm manager node to find on which node container for backups is running.

Deploy Grafana in a Docker Swarm using the command:

`docker stack deploy -c grafana-traefik-letsencrypt-docker-swarm.yml grafana`

# Author

I’m Vladimir Mikhalev, the [Docker Captain](https://www.docker.com/captains/vladimir-mikhalev/), but my friends can call me Valdemar.

🌐 My [website](https://www.heyvaldemar.com/) with detailed IT guides\
🎬 Follow me on [YouTube](https://www.youtube.com/channel/UCf85kQ0u1sYTTTyKVpxrlyQ?sub_confirmation=1)\
🐦 Follow me on [Twitter](https://twitter.com/heyValdemar)\
🎨 Follow me on [Instagram](https://www.instagram.com/heyvaldemar/)\
🧵 Follow me on [Threads](https://www.threads.net/@heyvaldemar)\
🐘 Follow me on [Mastodon](https://mastodon.social/@heyvaldemar)\
🧊 Follow me on [Bluesky](https://bsky.app/profile/heyvaldemar.bsky.social)\
🎸 Follow me on [Facebook](https://www.facebook.com/heyValdemarFB/)\
🎥 Follow me on [TikTok](https://www.tiktok.com/@heyvaldemar)\
💻 Follow me on [LinkedIn](https://www.linkedin.com/in/heyvaldemar/)\
🐈 Follow me on [GitHub](https://github.com/heyvaldemar)

# Communication

👾 Chat with IT pros on [Discord](https://discord.gg/AJQGCCBcqf)\
📧 Reach me at ask@sre.gg

# Give Thanks

💎 Support on [GitHub](https://github.com/sponsors/heyValdemar)\
🏆 Support on [Patreon](https://www.patreon.com/heyValdemar)\
🥤 Support on [BuyMeaCoffee](https://www.buymeacoffee.com/heyValdemar)\
🍪 Support on [Ko-fi](https://ko-fi.com/heyValdemar)\
💖 Support on [PayPal](https://www.paypal.com/paypalme/heyValdemarCOM)
