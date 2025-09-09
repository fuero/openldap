FROM debian:trixie


# Install OpenLDAP
RUN bash <<EOF
set -euo pipefail
apt update
export DEBIAN_FRONTEND=noninteractive
apt install -y \
      slapd ldap-utils openssl ca-certificates \
      slapd-contrib tini procps
apt clean
rm -rf /var/cache/apt
EOF

# Copy project files
COPY resources /app

# Change to /app/
WORKDIR /app/

# Run your program under Tini
ENTRYPOINT ["/usr/bin/tini", "--"]
CMD ["/app/entrypoint.sh"]
