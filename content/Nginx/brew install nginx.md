```
==> Renamed Formulae
ark -> velero                                                                       gloo-ctl -> glooctl
==> Deleted Formulae
at-spi2-atk          gdnsd                go@1.8               monax                plan9port            protobuf@2.6         solr@5.5             tmux-cssh
at-spi2-core         go@1.4               libutf               pdftoedn             protobuf@2.5         ruby@2.3             solr@6.6             zxing-cpp

==> Installing dependencies for nginx: openssl and pcre
==> Installing nginx dependency: openssl
==> Downloading https://homebrew.bintray.com/bottles/openssl-1.0.2r.high_sierra.bottle.tar.gz
==> Downloading from https://akamai.bintray.com/2b/2b68bd92c0c2faea5a1e70cc57a2403482ab2d83d0201bb42016c57c754427a5?__gda__=exp=1555223808~hmac=7d42885acb1aa9e94b1d7c6
######################################################################## 100.0%
==> Pouring openssl-1.0.2r.high_sierra.bottle.tar.gz
==> Caveats
A CA file has been bootstrapped using certificates from the SystemRoots
keychain. To add additional certificates (e.g. the certificates added in
the System keychain), place .pem files in
  /usr/local/etc/openssl/certs

and run
  /usr/local/opt/openssl/bin/c_rehash

openssl is keg-only, which means it was not symlinked into /usr/local,
because Apple has deprecated use of OpenSSL in favor of its own TLS and crypto libraries.

If you need to have openssl first in your PATH run:
  echo 'export PATH="/usr/local/opt/openssl/bin:$PATH"' >> ~/.zshrc

For compilers to find openssl you may need to set:
  export LDFLAGS="-L/usr/local/opt/openssl/lib"
  export CPPFLAGS="-I/usr/local/opt/openssl/include"

==> Summary
🍺  /usr/local/Cellar/openssl/1.0.2r: 1,795 files, 12.1MB
==> Installing nginx dependency: pcre
==> Downloading https://homebrew.bintray.com/bottles/pcre-8.43.high_sierra.bottle.tar.gz
==> Downloading from https://akamai.bintray.com/03/0389911a93a88efd4a69b52dea8ecb872fdb55bcfff45d2f7313be5f79730861?__gda__=exp=1555223825~hmac=c70fce4e171481df7b23d59
######################################################################## 100.0%
==> Pouring pcre-8.43.high_sierra.bottle.tar.gz
🍺  /usr/local/Cellar/pcre/8.43: 204 files, 5.5MB
==> Installing nginx
==> Downloading https://homebrew.bintray.com/bottles/nginx-1.15.11.high_sierra.bottle.tar.gz
==> Downloading from https://akamai.bintray.com/36/3654e93805660f9eaef26ee986db315ba0d33ee7f0d7f72f913e5ae5cdb65a2d?__gda__=exp=1555223833~hmac=f196cee928682537f31e054
######################################################################## 100.0%
==> Pouring nginx-1.15.11.high_sierra.bottle.tar.gz
==> Caveats
Docroot is: /usr/local/var/www

The default port has been set in /usr/local/etc/nginx/nginx.conf to 8080 so that
nginx can run without sudo.

nginx will load all files in /usr/local/etc/nginx/servers/.

To have launchd start nginx now and restart at login:
  brew services start nginx
Or, if you don't want/need a background service you can just run:
  nginx
==> Summary
🍺  /usr/local/Cellar/nginx/1.15.11: 25 files, 2MB
==> `brew cleanup` has not been run in 30 days, running now...
Removing: /usr/local/Cellar/openssl/1.0.2q... (1,794 files, 12.1MB)
Removing: /Users/fh/Library/Caches/Homebrew/openssl--1.0.2q.high_sierra.bottle.tar.gz... (3.7MB)
Removing: /usr/local/Cellar/pcre/8.42... (204 files, 5.3MB)
Removing: /Users/fh/Library/Caches/Homebrew/python--3.7.2_1.high_sierra.bottle.1.tar.gz... (14.4MB)
Removing: /Users/fh/Library/Caches/Homebrew/sqlite--3.26.0_1.high_sierra.bottle.1.tar.gz... (1.8MB)
Removing: /Users/fh/Library/Caches/Homebrew/watchman--4.9.0_1.high_sierra.bottle.tar.gz... (543.0KB)
Removing: /Users/fh/Library/Logs/Homebrew/pandoc... (64B)
Removing: /Users/fh/Library/Logs/Homebrew/go... (64B)
Removing: /Users/fh/Library/Logs/Homebrew/maven... (101B)
Removing: /Users/fh/Library/Logs/Homebrew/watchman... (303B)
Pruned 0 symbolic links and 3 directories from /usr/local
==> Caveats
==> openssl
A CA file has been bootstrapped using certificates from the SystemRoots
keychain. To add additional certificates (e.g. the certificates added in
the System keychain), place .pem files in
  /usr/local/etc/openssl/certs

and run
  /usr/local/opt/openssl/bin/c_rehash

openssl is keg-only, which means it was not symlinked into /usr/local,
because Apple has deprecated use of OpenSSL in favor of its own TLS and crypto libraries.

If you need to have openssl first in your PATH run:
  echo 'export PATH="/usr/local/opt/openssl/bin:$PATH"' >> ~/.zshrc

For compilers to find openssl you may need to set:
  export LDFLAGS="-L/usr/local/opt/openssl/lib"
  export CPPFLAGS="-I/usr/local/opt/openssl/include"

==> nginx
Docroot is: /usr/local/var/www

The default port has been set in /usr/local/etc/nginx/nginx.conf to 8080 so that
nginx can run without sudo.

nginx will load all files in /usr/local/etc/nginx/servers/.

To have launchd start nginx now and restart at login:
  brew services start nginx
Or, if you don't want/need a background service you can just run:
  nginxZZ
```



# nginx: [emerg] bind() to 0.0.0.0:80 failed (13: Permission denied)

nginx: the configuration file /home/work/local-qc/nginx/conf/nginx.conf syntax is ok
nginx: [emerg] bind() to 0.0.0.0:80 failed (13: Permission denied)
nginx: configuration file /home/work/local-qc/nginx/conf/nginx.conf test failed



原因：当前用户对该位置没有写入权限

解决办法：

1.使用命令：sudo /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf 以root权限启动

2.使用命令：sudo chmod -R a+rw /usr/local/nginx 给所有用户赋权限（个人学习，不考虑安全问题）

​                    /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf  启动Nginx



注：以非root权限启动时，会出现 nginx: [emerg] bind() to 0.0.0.0:80 failed (13: Permission denied) 错误

原因：Linux只有root用户可以使用1024一下的端口

解决办法：1.已root权限启动

  2.将 /usr/local/nginx/conf/nginx.conf 文件中的80端口改为1024以上

server {

\# listen 80

   listen 8080

……

}

