```
cacti	cacti/app-password-confirm	password	
# MySQL application password for cacti:
cacti	cacti/mysql/app-pass	password	
cacti	cacti/mysql/admin-pass	password	
cacti	cacti/password-confirm	password	
# MySQL database name for cacti:
cacti	cacti/db/dbname	string	cacti
# Connection method for MySQL database of cacti:
cacti	cacti/mysql/method	select	Unix socket
# Host running the MySQL server for cacti:
cacti	cacti/remote/newhost	string	
# Configure database for cacti with dbconfig-common?
cacti	cacti/dbconfig-install	boolean	true
cacti	cacti/remote/port	string	
cacti	cacti/internal/skip-preseed	boolean	false
# Delete the database for cacti?
cacti	cacti/purge	boolean	false
cacti	cacti/webserver	select	apache2
# Back up the database for cacti before upgrading?
cacti	cacti/upgrade-backup	boolean	true
# Reinstall database for cacti?
cacti	cacti/dbconfig-reinstall	boolean	false
# MySQL username for cacti:
cacti	cacti/db/app-user	string	cacti
cacti	cacti/install-error	select	abort
# Perform upgrade on database for cacti with dbconfig-common?
cacti	cacti/dbconfig-upgrade	boolean	true
cacti	cacti/upgrade-error	select	abort
cacti	cacti/remove-error	select	abort
# Host name of the MySQL database server for cacti:
cacti	cacti/remote/host	select	localhost
# Database type to be used by cacti:
cacti	cacti/database-type	select	mysql
# Deconfigure database for cacti with dbconfig-common?
cacti	cacti/dbconfig-remove	boolean	true
cacti	cacti/mysql/admin-user	string	debian-sys-maint
cacti	cacti/internal/reconfiguring	boolean	false
cacti	cacti/missing-db-package-error	select	abort
cacti	cacti/passwords-do-not-match	error	
```


----------
### :books: 參考網站：
- [unix_configure_cacti](http://www.cacti.net/downloads/docs/html/unix_configure_cacti.html)
