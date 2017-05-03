# BOSH release for ngrok

https://ngrok.com/ offers secure tunnels. This BOSH release runs ngrok to make an internal service publicly accessible.

## Usage

### Ngrok limits

NOTE: free https://ngrok.com accounts only allow a single tunnel. If you do not use a paid Ngrok account may experience bosh deployment failures caused by `ngrok` job:

```
22:46:48 | Updating instance myapp: myapp/d7a5f5a3-df89-4e28-97a3-bd77981902d3 (0) (00:01:22)
            L Error: 'myapp/0 (d7a5f5a3-df89-4e28-97a3-bd77981902d3)' is not running after update. Review logs for failed jobs: ngrok
```

If you look in the failing job's `ngrok` logs you will see the error:

```
t=2017-05-03T22:50:17+0000 lvl=crit msg="command failed" err="Tunnel session failed: Your account 'Dr Nic Williams' is limited to 1 simultaneous ngrok client session.\nActive ngrok client sessions in region 'us':\n  - 30a76e7a24f567ce0db743a27b746274 (185.99.186.162:41484)"
Tunnel session failed: Your account 'Dr Nic Williams' is limited to 1 simultaneous ngrok client session.
Either delete other deployments using https://ngrok.com first, or upgrade your ngrok account.
```
