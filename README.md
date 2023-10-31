# aca-devops

# This is load balancer config
# I have tryed to add the health_check but I have got error that the health_check directive not allowed here

# Virtual Host configuration for example.com
#
# You can move that to a different file under sites-available/ and symlink that
# to sites-enabled/ to enable it.
#
upstream loadbalancing {
   server acaserver1.example.com max_fails=3 weight=3;
   server acaserver2.example.com;
}
server {
   listen 80;
   listen [::]:80;

   server_name aca.example.com;

   location / {
       proxy_pass http://loadbalancing;
#       proxy_http_version 1.1;
#       proxy_set_header   Connection "";
#       health_check;
#       proxy_connect_timeout 2s;
#       proxy_read_timeout 3s;
   }
}
