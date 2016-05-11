### Apply patches

```
cd /opt/gitlab/embedded/service/gitlab-rails
git clone https://github.com/ludios/gitlab-patches
git am gitlab-patches/*.patch
```

### Rebuild compiled CSS files

```
cd /opt/gitlab/embedded/service/gitlab-rails && \
chmod -R a+rX app config/initializers && \
setfacl -R -m u:git:rwX public/assets && \
gitlab-rake assets:precompile RAILS_ENV=production && \
gitlab-ctl restart
```
