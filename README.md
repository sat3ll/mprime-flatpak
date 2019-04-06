# Installation

## Installing:
```
flatpak-builder builddir org.mersenne.mprime.yml --force-clean --install --user
```

## Running:
```
flatpak run org.mersenne.mprime
```

## Running as a daemon (systemd):
Create a file at `/etc/systemd/system/mprime.service` with the following content:
```
[Unit]
Description=Mersenne Primality Tester

[Service]
Type=simple
User=<user>
ExecStart=sh -c 'flatpak run --command=mprime-daemon org.mersenne.mprime 2>&1'
KillMode=process
KillSignal=SIGTERM

[Install]
WantedBy=multi-user.target
```
Replace `<user>` with your username.  
Before activating mprime.service, you should run mprime at least once
to set your preferences!


##### Start the service automatically at boot:
```
systemctl enable mprime.service
```

##### Activate the service with:
```
systemctl start mprime.service
```

##### Stop it with:
```
systemctl stop mprime.service
```

##### Look at daemon logs:
```
journalctl -fu mprime
```
