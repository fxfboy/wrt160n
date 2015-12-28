# Install Redsocks2

Redsocks is a transparent proxy, the current Redsocks2 supports the Shadowsocks server

### Download redsocks2
[Redsocks2 for DD-WRT](https://github.com/fxfboy/wrt160n/tree/master/redsocks)


### Redsocks2 configuration
	base {
		log_debug = off;
		log_info = on;
		log = stderr;
		daemon = on;
		redirector = iptables;
	}

	redsocks {
		local_ip = 192.168.1.1;//router's lan ip
		local_port = 1080;

		ip = x.x.x.x;//Shadowsocks server's ip

		port = 8388;

		type = shadowsocks;

		autoproxy = 1;
		timeout = 8;

		login = "aes-256-cfb";//Shadowsocks crypt method
		password = "xxxxxx";//Shadowsocks crypt password
	}

	//Following are Optinal

	autoproxy {
	    no_quick_check_seconds = 300;
	    quick_connect_timeout = 2;
	}
		                   
	ipcache {
	    cache_size = 4;
	    stale_time = 900;
	    port_check = 1;
	    cache_file = "/tmp/ipcache.txt";
	    autosave_interval = 3600;
	}


### iptables rules
	iptables -t nat -N REDSOCKS
	iptables -t nat -A REDSOCKS -d 0.0.0.0/8 -j RETURN
	iptables -t nat -A REDSOCKS -d 10.0.0.0/8 -j RETURN
	iptables -t nat -A REDSOCKS -d 127.0.0.0/8 -j RETURN
	iptables -t nat -A REDSOCKS -d 169.254.0.0/16 -j RETURN
	iptables -t nat -A REDSOCKS -d 172.16.0.0/12 -j RETURN
	iptables -t nat -A REDSOCKS -d 192.168.0.0/16 -j RETURN
	iptables -t nat -A REDSOCKS -d 224.0.0.0/4 -j RETURN
	iptables -t nat -A REDSOCKS -d 240.0.0.0/4 -j RETURN
	iptables -t nat -A REDSOCKS -p tcp -j REDIRECT --to-ports 1080
	iptables -t nat -I PREROUTING -j REDSOCKS
