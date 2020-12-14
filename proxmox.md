# Proxmox

# Using device without 1:1 nics

Implemented if Proxmox VE server at hosting provider, with a single public IP address.

Masquerading allows guests having only a private IP address to access the network by using the host IP address for outgoing traffic. Each outgoing packet is rewritten by iptables to appear as originating from the host, and responses are rewritten accordingly to be routed to the original sender.
