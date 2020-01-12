## Setting up Jekyll locally on Windows
 
Start with a basic Ubuntu docker image with the GH-page repo bind-mounted to /blog

```
docker run -v D:\Data-Disk-Enc\git-github\StianOvrevage\cv:/cv -p4000:4000 --rm -it ubuntu
```

Install some stuff in the container and start the dev-server.
```
apt-get update
apt-get install -y ruby-dev make gcc zlib1g-dev libcurl3 git
gem install bundler
gem update --system
cd cv
bundle install

bundle exec jekyll _3.6.2_ new cv # Only for un-initialized sites
mv cv/* .

git clone https://github.com/sharu725/online-cv
mv online-cv/* .

bundle update
bundle exec jekyll serve --host 0.0.0.0
```

Go to http://localhost:4000/ to preview.

### Tips

Locate UTF8-content in files: `grep --color='auto' -P -n "[\x80-\xFF]" *`

