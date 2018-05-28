# devops-reverse-proxy

Steps:

1. changes in the /conf/httpd.conf file
 Make Listen port to 8080
 Un-comment the proxy modules  in httpd.conf file
 
LoadModule proxy_module modules/mod_proxy.so

LoadModule proxy_ajp_module modules/mod_proxy_ajp.so

LoadModule proxy_balancer_module modules/mod_proxy_balancer.so

LoadModule proxy_connect_module modules/mod_proxy_connect.so

LoadModule proxy_ftp_module modules/mod_proxy_ftp.so

LoadModule proxy_http_module modules/mod_proxy_http.so

LoadModule proxy_scgi_module modules/mod_proxy_scgi.so

Place vhosts folder (contains : 000_localhost.conf file) inside conf directory & include in httpd.conf file
Include conf/vhosts/*.conf

           Add revers proxy VirtualHost section in  000_localhost.conf  file

           <VirtualHost *:8080>
	DocumentRoot "/usr/local/apache2/htdocs"
	ServerName localhost
	 
	SSLProxyEngine on
	
	ProxyPass "/emojis" "https://api.github.com/emojis"
	ProxyPassReverse  "/emojis" "https://api.github.com/emojis"
	ProxyPass "/transit" "https://transit.land/api/v1"
	ProxyPassReverse "/transit" "https://transit.land/api/v1"
</VirtualHost>
