# shadowsocks-libev-archlinux

it is PKGBUILD for arch linux when you want to get newest commit of shadowsocks-libev

setcap \
			cap_net_bind_service+ep /usr/bin/ss-local \
			cap_net_bind_service,cap_net_admin+ep /usr/bin/ss-redir \
			cap_net_bind_service+ep /usr/bin/ss-server \
			cap_net_bind_service+ep /usr/bin/ss-tunnel
