# issue

To reproduce the issue outside Dependabot run:

`npm install vue@2.7.13 --force`

To reproduce the issue with Dependabot run:

`dependabot update --dry-run -f input.yaml --debug`

Then run `bin/run fetch_files` followed by `bin/run update_files`. Once you notice the proxy output freezes, ctl-c reveals the stack trace:

```
^C#<Thread:0x0000ffff9012fee0 /usr/local/lib/ruby/3.1.0/open3.rb:404 run> terminated with exception (report_on_exception is true):
/usr/local/lib/ruby/3.1.0/open3.rb:404:in `read': stream closed in another thread (IOError)
        from /usr/local/lib/ruby/3.1.0/open3.rb:404:in `block (2 levels) in capture2e'
/usr/local/lib/ruby/3.1.0/open3.rb:416:in `value': Interrupt
        from /usr/local/lib/ruby/3.1.0/open3.rb:416:in `block in capture2e'
        from /usr/local/lib/ruby/3.1.0/open3.rb:228:in `popen_run'
        from /usr/local/lib/ruby/3.1.0/open3.rb:210:in `popen2e'
        from /usr/local/lib/ruby/3.1.0/open3.rb:399:in `capture2e'
        from /home/dependabot/common/lib/dependabot/shared_helpers.rb:301:in `run_shell_command'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:208:in `run_npm8_top_level_updater'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:160:in `run_npm_top_level_updater'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:149:in `block in run_npm_updater'
        from /home/dependabot/common/lib/dependabot/shared_helpers.rb:168:in `with_git_configured'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:146:in `run_npm_updater'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:115:in `run_current_npm_update'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:60:in `block (2 levels) in updated_lockfile_content'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:60:in `chdir'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:60:in `block in updated_lockfile_content'
        from /home/dependabot/common/lib/dependabot/shared_helpers.rb:49:in `block in in_a_temporary_directory'
        from /home/dependabot/common/lib/dependabot/shared_helpers.rb:49:in `chdir'
        from /home/dependabot/common/lib/dependabot/shared_helpers.rb:49:in `in_a_temporary_directory'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:58:in `updated_lockfile_content'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater/npm_lockfile_updater.rb:29:in `updated_lockfile'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater.rb:242:in `updated_lockfile_content'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater.rb:169:in `package_lock_changed?'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater.rb:198:in `block in updated_lockfiles'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater.rb:197:in `each'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater.rb:197:in `updated_lockfiles'
        from /home/dependabot/npm_and_yarn/lib/dependabot/npm_and_yarn/file_updater.rb:40:in `updated_dependency_files'
        from /home/dependabot/dependabot-updater/lib/dependabot/updater.rb:739:in `generate_dependency_files_for'
        from /home/dependabot/dependabot-updater/lib/dependabot/updater.rb:303:in `check_and_create_pull_request'
        from /home/dependabot/dependabot-updater/lib/dependabot/updater.rb:101:in `check_and_create_pr_with_error_handling'
        from /home/dependabot/dependabot-updater/lib/dependabot/updater.rb:72:in `block in run'
        from /home/dependabot/dependabot-updater/lib/dependabot/updater.rb:72:in `each'
        from /home/dependabot/dependabot-updater/lib/dependabot/updater.rb:72:in `run'
        from /home/dependabot/dependabot-updater/lib/dependabot/update_files_job.rb:17:in `perform_job'
        from /home/dependabot/dependabot-updater/lib/dependabot/base_job.rb:50:in `run'
        from bin/update_files.rb:23:in `<main>'

```
