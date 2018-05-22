---
layout: post
title: Upgrading PostgreSQL on macOS
---

Follow these easy steps to upgrade your PostgreSQL without losing your data. For this post, I'm upgrading from 9.6.2 to 10.4!

#### 1. Shut down PostgreSQL server

Assuming you are using Homebrew.

```
brew services stop postgresql
```

#### 2. Update PostgreSQL

Use Homebrew to upgrade your PostgreSQL.

```
brew update && brew upgrade postgresql
```

#### 3. Initialize a new data directory

To upgrade PostgreSQL and keep our old data, we need to migrate data from the old data directory to a new one. In order to do that, we need to create a new data directory first.

```
initdb /usr/local/var/postgres10.4 -E utf8
```

#### 4. Migrate old data from old directory to new one

This can be done using `pg_upgrade`, we just need to specify the old data and executable directory (-d and -b), the new data and executable directory (-D and -B). Read more on `pg_upgrade` [here](https://www.postgresql.org/docs/9.6/static/pgupgrade.html){:target="_blank" rel="noopener"}.

```
pg_upgrade \
-d /usr/local/var/postgres \
-D /usr/local/var/postgres10.4 \
-b /usr/local/Cellar/postgresql/9.6.2/bin/ \
-B /usr/local/Cellar/postgresql/10.4/bin/ \
-v
```

#### 5. Rename the data directory

PostgreSQL will look for postgres directory, so we just need to rename our new directory. 

```
cd /usr/local/var
# rename the old postgres to postgres9.6.2 as back up
mv postgres postgres9.6.2
# rename our new data directory to postgres
mv postgres10.4 postgres
```

#### 6. Start PostgreSQL back up

```
brew services start postgresql
```

With that, our PostgreSQL server should be live with all of our old data. 