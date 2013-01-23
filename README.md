redmine-recipes
===============

Setup files for redmine + unicorn + nginx.
(strongly influenced by gitlab and gitlab-recipe)


## unicorn

### install
```sh
sudo -u redmine cp Gemfile.local /home/redmine/redmine
sudo -u redmine bundle install -without development test
```
### configration
```sh
sudo -u redmine cp unicorn.rb /home/redmine/redmine/conf/unicorn.rb
```


## nginx

### install
```sh
sudo apt-get install nginx
```

### configuration
```sh
sudo cp nginx/redmine /etc/nginx/sites-available
# Change YOUR_SERVER_IP, PORT, YOUR_SERVER_FQDN for your environment
sudo vi nginx/redmine /etc/nginx/sites-available/redmine
sudo ln -s /etc/nginx/sites-available/redmine /etc/nginx/sites-enabled/redmine
```

### restart
```
sudo /etc/init.d/nginx restart
```


## service

### install
```sh
sudo cp init.d/redmine /etc/init.d
sudo chmod +x /etc/init.d/redmine
```

### start
```sh
sudo service redmine start
```
