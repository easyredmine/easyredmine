# Easy Redmine

Easy Redmine - plugin to Redmine (http://www.redmine.org)
Copyright (C) 2008-2013  Easy Software, s.r.o.
https://www.easyredmine.com


## Requirements

Same as Redmine 2.3.1. See [redmine_root]/doc/INSTALL
Only Ruby 1.8.7 (will be deprecated soon) or 1.9.3 are supported.

Installing Redmine and Easy Redmine to virtual directory like http://localhost/redmine is not working.

## Installation

1. Make sure your Redmine 2.3.1 is working.
   For more details visit http://www.redmine.org/projects/redmine/wiki/Installation_Guide.

2. Backup your Redmine database and folder if something make wrong.

3. Extract zip package to the Redmine plugins directory ([redmine_root]/plugins). 
   The directory structure will look like:
     [redmine_root]/plugins/easyproject/easy_helpers/*
     [redmine_root]/plugins/easyproject/easy_plugins/easy_extensions/*
     [redmine_root]/plugins/easyproject/easy_plugins/easy_redmine/*
     [redmine_root]/plugins/easyproject/easy_plugins/*  

4. More gems are required. Under the application main directory run: 
     bundle install --without development test
   
   If ImageMagick is not installed on your system, you should skip the installation
   of the rmagick gem using:
     bundle install --without development test rmagick

5. Under the application main directory run (if you are using bitnami write 'sudo' before 'bundle'):
     bundle exec rake easyproject:install RAILS_ENV=production
   
6. If you are migrating from older Ruby version < 1.9 (e.g. 1.8.7) to Ruby version >= 1.9 you have to run:
     bundle exec rake easyproject:service_tasks:migrate_to_new_ruby RAILS_ENV=production

7. Start your Redmine application server. E.g. under the application main directory run:
     bundle exec ruby script/rails server -e production

8. You should create a maintanance task to CRON (on Linux) or Scheduled Tasks (on Windows) that
   will be running every 5-15 minutes. This one task aggregates all required tasks such as mail receiving,
   alerts evaluation etc. You should set up required parameters via administration -> scheduled tasks.
   Do not run this task under root, use same user that is used for web server.:
     bundle exec rake easyproject:scheduler:run_tasks RAILS_ENV=production

## Notes

Easy Redmine is tested only on MySQL server.

## References

Changelog is on: http://www.easyredmine.com/news
Feaures are on: http://www.easyredmine.com/features
Support is on: http://www.easyredmine.com/support
