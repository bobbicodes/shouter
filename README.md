# shouter

The awesome [Heroku tutorial](https://devcenter.heroku.com/articles/clojure-web-application)

## Local database setup

This is all sorts of weird. But some combination of the following resulted in success:

```
sudo apt install postgresql
/usr/lib/postgresql/10/bin/initdb pg
postgres -D pg &
/usr/lib/postgresql/10/bin/pg_ctl -D pg -l logfile start
sudo chown -R postgres:postgres /var/run/postgresql
/usr/lib/postgresql/10/bin/pg_ctl -D pg -l logfile start
sudo pkill -u postgres
/usr/lib/postgresql/10/bin/pg_ctl -D pg -l logfile start
sudo chown -R porky:porky /var/run/postgresql
/usr/lib/postgresql/10/bin/pg_ctl -D pg -l logfile start
createdb shouter
lein repl
lein run -m shouter.web
lein uberjar
java $JVM_OPTS -jar target/shouter-standalone.jar
git init
git add .
git commit -m "init"
heroku create
heroku addons:create heroku-postgresql
git push heroku master
git remote add origin git@github.com:porkostomus/shouter.git
git push -u origin master

```

## Usage

[Live app](http://still-cove-47517.herokuapp.com/)

## License

Copyright © 2019 FIXME

This program and the accompanying materials are made available under the
terms of the Eclipse Public License 2.0 which is available at
http://www.eclipse.org/legal/epl-2.0.

This Source Code may also be made available under the following Secondary
Licenses when the conditions for such availability set forth in the Eclipse
Public License, v. 2.0 are satisfied: GNU General Public License as published by
the Free Software Foundation, either version 2 of the License, or (at your
option) any later version, with the GNU Classpath Exception which is available
at https://www.gnu.org/software/classpath/license.html.
