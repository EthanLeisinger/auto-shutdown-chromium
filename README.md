# Chromium Shutdown `systemd` Service

## What and Why?

This `systemd` service is inteneded to automatically shutdown all
Chromium services gracefully when the system shutsdown.

## How?

This project includes a `systemd` service that will need to be added to
the `systemd` config and an executable that will need to be linked into `/bin`.
You can see more details on setup in the [Setup section](#installsetup)

## Install/Setup

Clone this repo to any directory you prefer. Then run the following commands:

```shell
sudo ln -s ./shutdown-chromium /bin/
sudo ln -s ./shutdown-chromium.service /etc/systemd/service/
sudo systemctl enable "$PWD/shutdown-chromium.service"
```

## Uninstall

If you would like to uninstall this script or delete/move this repo, ensure you
disable the `systemd` service and remove the symlink to the script from `/bin/`. This can be done with:

```shell
sudo systemctl diable shutdown-chromium.service
sudo rm /bin/shutdown-chromium/
```

Once this is complete you are free to delete this repo as you wish.

## Can this do more?

Yes! This script is really simple and can be extended to automatically shutdown
any process that does not shutdown gracefully on Linux. Chrome is the one that
is most notorious for this issue to me.
