chef-diaspora
=============

Chef Cookbook for Diaspora

Depends:
 * mysql
 * chef_handler
 * user
 * nginx
 * minitest
 * chef-solo-search (if using chef solo)
 * git
 
Due to the complexity of the Ruby environment, I leave that up to you!
(I simply use what comes on the box by default for Amazon EC2 Ubuntu 12.10)
 
My Role JSON Looks like:
```json
"run_list": [
	"recipe[php]",
	"recipe[chef-solo-search]",
	"recipe[user::data_bag]",
	"recipe[nginx]",
	"recipe[mysql::server]",
	"recipe[diaspora]"
],
"diaspora" : {
   "dir" : "/opt/diaspora",
   "pod_name" : "anthroprose",
   "domain" : "me.anthroprose.com",
   "url" : "https://me.anthroprose.com",
   "admin" : "anthroprose",
   "admin_email" : "anthroprose@gmail.com",
   "enable_registrations" : "false",
   "require_ssl" : "false",
   "city" : "Austin",
   "state" : "TX",
   "dependencies" : [
		"build-essential",
		"libxslt1.1",
		"libxslt1-dev",
		"libxml2",
		"libmysqlclient-dev",
		"libmysql-ruby",
		"libssl-dev",
		"libopenssl-ruby",
		"libcurl4-openssl-dev",
		"imagemagick",
		"libmagickwand-dev",
		"git-core",
		"redis-server",
		"libffi-dev",
		"libffi-ruby",
		"libsqlite3-dev",
		"libpq-dev",
		"libreadline5",
		"openjdk-7-jre",
		"nodejs",
		"libncurses5-dev"
	]
}
```

The databag at: data_bags/diaspora/config.json looks like:
```pre
{
    "id" : "config",
    "diaspora_facebook_enable" : "true",
    "diaspora_facebook_app_id" : "xxxxxxxxxxxxxxxxx",
    "diaspora_facebook_secret" : "xxxxxxxxxxxxxx"
}

```