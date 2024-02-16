# homelab-mariadb
this is the setup i use for my home lab mariadb instance

mariadb.home.arpa is the node it should run on.  I am using block storage set up on this specific node (iscsi volume on /mnt/swarm/), so even though mariadb.home.arpa is in the swarm cluster (so it can access secrets and share networking) the database is not intended to float around on shared storage (nfs is not good for databases).

mariadb is not accessible outside the swarm cluster - for a container to have access it has to be added to the mariadb-net network.

pending: 
build a custom docker image and host it on a private/internal registry
the custom image should
pull CA certs from vault on startup
generate hosting certs from vault on startup
renew hosting certs periodically/as needed
automatic backups
offsite backups