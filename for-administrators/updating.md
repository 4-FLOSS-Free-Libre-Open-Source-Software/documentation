---
title: "Updating"
description: "Invidious's Updating documentation."
lead: "Invidious's Updating documentation."
date:
lastmod:
draft: false
images: []
menu:
  docs:
    parent: "for-administrators"
weight: 100
toc: true
---

## Invidious releases are based on tags. You can use them if you want to be sure your instance is stable.

#### With release tags
```bash
$ sudo -i -u invidious
$ cd invidious
$ currentVersion=$(git rev-list --max-count=1 --abbrev-commit HEAD)
$ git pull
$ latestVersion=$(git describe --tags --abbrev=0)
$ git checkout $latestVersion
$ for i in `git rev-list --reverse --abbrev-commit $currentVersion..HEAD` ; do file=./config/migrate-scripts/migrate-db-$i.sh ; [ -f $file ] && $file ; done
$ shards update && shards install
$ crystal build src/invidious.cr --release
$ exit
$ sudo systemctl restart invidious.service
```

#### With master branch
```bash
$ sudo -i -u invidious
$ cd invidious
$ currentVersion=$(git rev-list --max-count=1 --abbrev-commit HEAD)
$ git pull
$ for i in `git rev-list --reverse --abbrev-commit $currentVersion..HEAD` ; do file=./config/migrate-scripts/migrate-db-$i.sh ; [ -f $file ] && $file ; done
$ shards update && shards install
$ crystal build src/invidious.cr --release
$ exit
$ sudo systemctl restart invidious.service
```

#### With Docker:
```bash
$ docker-compose pull && docker-compose up --force-recreate --build && docker image prune -f
```
