# luci-app-frps

Luci support for Frps, inspire by [kuoruan/luci-app-frpc](https://github.com/kuoruan/luci-app-frpc). Included in [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede).

- support daemon process via procd
- support most frps‘setting in LuCi, including TLS-only (frps_v0.34.0+).
- support other frps‘setting via “extra setting” (Format: option=value)

## Install

1. Download ipk files from [release page](https://github.com/lwz322/luci-app-frps/releases)

2. Upload files to your router.

3. Install package with opkg:

```sh
opkg install luci-app-frps_*.ipk
```

## Configure

1. Download client file from Frp release [link](https://github.com/fatedier/frp/releases) or Frp ipk release [link](https://github.com/kuoruan/openwrt-frp/releases).

2. Upload the client file to your router, or install the ipk file.

3. Config client file path in luci.

4. Add your server and proxy rules.

5. Enable the client.

## Known issue

- Config validate failed when install *ipk
```shell
root@K3:~# opkg install ./luci-app-frps*
Installing luci-app-frps (0.0.1-1) to root...
Configuring luci-app-frps.
frps.main.enabled=0 validates as bool with true
frps.main.client_file=/usr/bin/frps validates as file with false
frps.main.run_user is unset and defaults to string (null)
frps.main.enable_logging is unset and defaults to bool 0
frps.main.log_file is unset and defaults to string /var/log/frps.log
frps.main.log_level is unset and defaults to or("trace", "debug", "info", "warn", "error") warn
frps.main.log_max_days is unset and defaults to uinteger 3
frps.main.disable_log_color is unset and defaults to or("true", "false") (null)
frps.main.max_pool_count is unset and defaults to uinteger (null)
frps.main.max_ports_per_client is unset and defaults to uinteger 0
frps.main.subdomain_host is unset and defaults to host (null)
frps.main.dashboard_addr is unset and defaults to host (null)
frps.main.dashboard_port is unset and defaults to port (null)
frps.main.dashboard_user is unset and defaults to string (null)
frps.main.dashboard_pwd is unset and defaults to string (null)
frps.main.bind_port=7000 validates as port with true
frps.main.token is unset and defaults to string (null)
frps.main.tcp_mux=true validates as or("true", "false") with true
frps.main.bind_udp_port is unset and defaults to port (null)
frps.main.kcp_bind_port is unset and defaults to port (null)
frps.main.vhost_http_port is unset and defaults to port (null)
frps.main.vhost_https_port is unset and defaults to port (null)
[err] Config validate failed.
```

- when uninstall
```shell
root@K3:~# opkg remove luci-app-frps
Removing package luci-app-frps from root...
Not deleting modified conffile /etc/config/frps.
```