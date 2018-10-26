touch /etc/systemd/system/giantd.service

cat <<EOF >> /etc/systemd/system/giantd.service
[Unit]
Description=Giant
After=network.target
[Service]
Type=forking
User=root
WorkingDirectory=/root
ExecStart=/root/giant/giantd -conf=/root/.giant/giant.conf -datadir=/root/.giant
ExecStop=/root/giant/giant-cli -conf=/root/.giant/giant.conf -datadir=/root/.giant stop
Restart=on-failure
RestartSec=1m
StartLimitIntervalSec=5m
StartLimitInterval=5m
StartLimitBurst=3
[Install]
WantedBy=multi-user.target
EOF

sudo systemctl enable giantd
sudo systemctl start giantd
