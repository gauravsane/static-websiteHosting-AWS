# 1] TO Get Backup From Server
Remote → Local  rsync -avz -e "ssh -i /home/cloud/pem-file.pem" ubuntu@ip-address:/home/ubuntu/remote-dir /path/to/local/dir

eg. for getting "static" folder from server to local system rsync -avz -e "ssh -i /home/cloud/digi-test.pem" ubuntu@13.235.109.226:/home/ubuntu/static

# 2] Get backup from var/www 
= First Move the file to the home 

# 3] Configure Nginx file using vim
sudo vim /etc/nginx/site-available/default

Add Location block of static files under digilateral.com domain

eg. for digilateral.com/pagename configuration should look like this
location /pagename {   # what should be displayed on web mention here 
                alias /var/www/page; # mention the directory where main html file is present
                index index.html;  # point it to the main html file
                access_log /var/log/custom/page.log # Optional if you need access logs
    } 


# 4] this nginx config should come under

server {

listen  443  ssl  http2;

server_name digilateral.com www.domain.com;


## 5] Test and reload the nginx configuration 
1. Test the nginx
`sudo nginx -t`
2. Upon success reload the nginx 
`sudo systemctl reload nginx.service`




# 3] tail -f to see live logs
# 4] tail -f -n number to see logs

# 5] df -h to see server capacity storage (disk free)
# 6] du -sh file/folder see capacity  (disk Usage)
