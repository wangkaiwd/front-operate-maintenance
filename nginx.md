## nginx

* [nginx documentation](https://nginx.org/en/docs/)

### Install Nginx

* [Installation nginx](https://nginx.org/en/docs/install.html)
  * [RHEL/Centos](https://nginx.org/en/linux_packages.html#RHEL-CentOS)
  * [Official Red Hat/CentOS packages](https://www.nginx.com/resources/wiki/start/topics/tutorials/install/)
  * [macos](https://www.javatpoint.com/installing-nginx-on-mac): brew install nginx
* [install nginx throw error](https://superuser.com/questions/571871/sudo-yum-install-nginx-throws-cannot-retrieve-repository-metadata-repomd-xml)
  ![](https://cdn.jsdelivr.net/gh/wangkaiwd/drawing-bed/202206191157334.png)
  * [Alibaba Cloud Linux Overview](https://help.aliyun.com/document_detail/111881.htm?spm=a2c4g.11186623.0.0.399e3d12m9iTKv#concept-rgv-rvd-2hb)
  * Alibaba Cloud Linux 3 -> CentOS 8、RHEL 8

### Nginx Configuration

* [Beginner's Guide](https://nginx.org/en/docs/beginners_guide.html)

nginx -V:

* [Building nginx from sources](https://nginx.org/en/docs/configure.html)

look nginx config file and related folders:

```shell
rpm -ql nginx
```

### Location

> [location](https://nginx.org/en/docs/http/ngx_http_core_module.html#location)

* none: prefix string, location with the longest matching prefix is selected and remembered
* `~` modifier: for case-sensitive matching
* `~*` modifier: for case-insensitive matching
* `^~` modifier: If the longest matching prefix location has the `^~` modifier then regular expression are not checked
* `=` modifier: define an exact match of URI and location and the search terminates.

Illustrate the about by an example:

```text
location = / {
    [ configuration A ]
}

# prefix location
location / {
    [ configuration B ]
}

location /documents/ {
    [ configuration C ]
}

location ^~ /images/ {
    [ configuration D ]
}

location ~* \.(gif|jpg|jpeg)$ {
    [ configuration E ]
}
```

* `/` : A
* `index.html`: B
* `/documents/document.html`: C
* `/images/1.gif`:  D
* `/documents/1.jpg`: E

match order:

1. Checks locations defined using the prefix strings(prefix locations)
2. Among them, the location with the longest matching prefix is selected and remembered
3. Then regular expression are checked, in the order of their appearance in the configuration file
4. The search of regular expression terminates on the first match, and corresponding configuration is used
5. If no match with a regular expression is found then configuration of the prefix location remembered earlier is used

### Split nginx log

* nginx logrotate
* crontab: write shell script custom this logic
* pm2-logrotate
