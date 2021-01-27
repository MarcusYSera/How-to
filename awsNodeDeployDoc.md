[HomeBrew](https://garrettsyhampton.wordpress.com/2019/10/02/how-to-install-homebrew-on-amazon-linux/)

[Tutorial AWS EC2 w/nodejs](https://ourcodeworld.com/articles/read/977/how-to-deploy-a-node-js-application-on-aws-ec2-server)

[Medium Article on Vue.js, Nginx, SSL on Ubuntu](https://medium.com/@kornchotpitakkul/deploy-a-node-js-and-vue-js-with-nginx-ssl-on-ubuntu-465f31216dc9)

sudo apt-get update && sudo apt-get -y upgrade

curl -sL https://deb.nodesource.com/setup_15.x | sudo -E bash -
sudo apt-get install -y nodejs

clone directory to /home folder

`cd /home`

allow nginx access

`sudo chmod g+x /home/FOLDER`

git clone https://github.com/MarcusYSera/vue-recipe-app.git

install all node dependencies, then build (ensure build runs locally with serve -s dist)

[nodejs installer](https://github.com/nodesource/distributions/blob/master/README.md)

pm2- necessary when deploying the api, ie express-postgres api

nginx server set up:

sudo vi /etc/nginx/sites-available/vue

```
server {
  listen 80;
  server_name 54.241.74.76;
  index index.html;

  location / {
    root /home/vue-recipe-app/client/dist;
    index index.html;
    try_files $uri $uri/ /index.html;
  }
  error_page 500 502 503 504 /50x.html;
  location = /50x.html {
    root /usr/share/nginx/html;
  }
}
```

ensure /etc/nginx/nginx.conf contains

```
http{
  ...
  include /etc/nginx/sites-enabled/*;
}
```

create link between sites-available folder and sites-enabled, specifically for the vue file

`sudo ln -s /etc/nginx/sites-available/vue /etc/nginx/sites-enabled/vue`

check link
`sudo nginx -t`

restart nginx:

`sudo service nginx restart`
or
`sudo systemctl restart nginx`

Purchase Domain name, may need to wait an hour for domain to be verified for ssl

[download certbot](https://certbot.eff.org/)

to test out build:
`serve -s dist`
