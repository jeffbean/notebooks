Puppet
======

RPM:
http://yum.puppetlabs.com/el/6/products/Dashboard


needs a config/database.yml file and a config/settings.yml file. It ships with
functional examples of each, as config/database.yml.example and
config/settings.yml.example respectively.
x86_64/

Dashboard runners:
sudo -u puppet-dashboard env RAILS_ENV=production script/delayed_job -p dashboard -n 1 -m start
