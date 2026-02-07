# Cybersec-prospective.
A project for a cybersecurity student starting from zero.
#!/bin/bash

# =================================================================
# PROJECT: Firewall Interface Regulation
# DESCRIPTION: Basic configuration to allow DNS and HTTP traffic.
# AUTHOR: [Your Name / ctwrs1311-netizen]
# =================================================================

# 1. Reset all existing firewall rules to ensure a clean start
sudo ufw --force reset

# 2. Set Default Policies
# Deny all incoming traffic (security first) and allow all outgoing traffic
sudo ufw default deny incoming
sudo ufw default allow outgoing

# 3. ALLOW PORT 53 (DNS) 
# Essential for Domain Name Resolution (translating URLs to IPs)
# We open both UDP and TCP as per security best practices
sudo ufw allow 53/udp
sudo ufw allow 53/tcp

# 4. ALLOW PORT 80 (HTTP)
# Allows basic web traffic (Insecure web browsing, used for testing)
sudo ufw allow 80/tcp

# 5. ENABLE FIREWALL
# Apply the rules and start the service
sudo ufw --force enable

# 6. VERIFICATION
# Display the current status and active rules
echo "----------------------------------------------------"
echo "🛡️ Firewall configured: Ports 53 and 80 are now OPEN."
echo "All other ports (including port 83) are CLOSED."
echo "----------------------------------------------------"
sudo ufw status verbose
