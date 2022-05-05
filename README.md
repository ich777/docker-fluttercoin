# Fluttercoin Wallet in Docker optimized for Unraid
FlutterCoin may be a coin with the tried and true algorithm of scrypt, but it's definitely anything but ordinary.

This is a community driven triple hybrid coin and the very first to offer a highly secure network through: Proof of Work (Mining), Proof of Stake (Investing), and it's own highly innovative Proof of Transaction (Using).

**ATTENTION:** Please keep in mind that your wallet is stored in the created folder in your appdata directory/.fluttercoin/wallet.dat - I strongly recommend you to backup this file on a regular basis!

**IMPORT:** If you are already using FlutterCoin you can import your existing wallet by placing the 'wallet.dat' in the appdata directory for fluttercoin/.fluttercoin/wallet.dat (please let the container fully startup if you are using it for the first time and then shut it down before replacing the wallet.dat).

**UPDATED NOTICE:** The container will check on every start/restart if there is a newer version available.

## Env params
| Name | Value | Example |
| --- | --- | --- |
| DATA_DIR | Folder for Fluttercoin | /fluttercoin |
| EXTRA_PARAMS| Leave empty if not needed (eg: '-upnp', '-dns',... without quotes) | -bind=0.0.0.0 |
| UID | User Identifier | 99 |
| GID | Group Identifier | 100 |

## Run example
```
docker run --name Fluttercoin-Wallet -d \
    -p 8080:8080 -p 7408:7408 -p 7474:7474 \
    --env 'EXTRA_PARAMS=-bind=0.0.0.0' \
    --restart=unless-stopped \
    ich777/fluttercoin
```

### Webgui address: http://[SERVERIP]:[PORT]/vnc_auto.html

## Set VNC Password:
 Please be sure to create the password first inside the container, to do that open up a console from the container (Unraid: In the Docker tab click on the container icon and on 'Console' then type in the following):

1) **su $USER**
2) **vncpasswd**
3) **ENTER YOUR PASSWORD TWO TIMES AND PRESS ENTER AND SAY NO WHEN IT ASKS FOR VIEW ACCESS**

Unraid: close the console, edit the template and create a variable with the `Key`: `TURBOVNC_PARAMS` and leave the `Value` empty, click `Add` and `Apply`.

All other platforms running Docker: create a environment variable `TURBOVNC_PARAMS` that is empty or simply leave it empty:
```
    --env 'TURBOVNC_PARAMS='
```

#### Support Thread: https://forums.unraid.net/topic/83786-support-ich777-application-dockers/