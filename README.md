# gfwlist2domain
A single shell command to convert gfwlist to domain list.

```sh
curl -s -k https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt \
	|base64 -d \
	|sed -n '{
		s/^||\?//g;
		s/https\?:\/\///g;
		s/^\.//g;
		s/\*.*//g;
		s/\/.*//g;
		s/%.*//g;
		/^$/d;
		/^!.*/d;
		/^@.*/d;
		/^\[.*/d;
		/\.$/d;
		/^[^\.]*$/d;
		/^[0-9\.]*$/d;
		p
}' |sort |uniq
```

Or

```sh
wget -q --no-check-certificate -O- https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt \
	|base64 -d \
	|sed -n '{
		s/^||\?//g;
		s/https\?:\/\///g;
		s/^\.//g;
		s/\*.*//g;
		s/\/.*//g;
		s/%.*//g;
		/^$/d;
		/^!.*/d;
		/^@.*/d;
		/^\[.*/d;
		/\.$/d;
		/^[^\.]*$/d;
		/^[0-9\.]*$/d;
		p
}' |sort |uniq
```
