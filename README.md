# Puppet Syntax Checkers

All the scripts were taken from [drwhal/puppet-git-hooks](https://github.com/drwahl/puppet-git-hooks) with almost no changes.

## Current supported pre-receive (server side) checks

* Puppet manifest syntax
* ERB and EPP template syntax
* Ruby syntax
* Puppet-lint
* YAML and JSON (hieradata) syntax
* Puppetfile syntax

## Usage

Validate Puppet code on the version control server with a pre-receive git hook.

### BitBucket

- Install the required gems in the BitBucket server
- Clone this project and ensure the scripts have execution permissions
- Enforce the main script, puppet_syntax_checkers.sh at the pre-receive git stage

I use the plugin [external hooks](https://marketplace.atlassian.com/plugins/com.ngs.stash.externalhooks.external-hooks/server/overview)

```
★ lmacchi@Pulpo 13:53:42 /tmp/puppet/control-repo> (production) git push origin production
Counting objects: 12, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (12/12), done.
Writing objects: 100% (12/12), 1.05 KiB | 1.05 MiB/s, done.
Total 12 (delta 6), reused 0 (delta 0)
remote: site/profile/manifests/base.pp - WARNING: double quoted string containing no variables on line 41
remote: site/profile/manifests/base.pp - ERROR: single quoted string containing a variable found on line 42
remote: Error: styleguide violation in site/profile/manifests/base.pp (see above)
remote: Error: 2 styleguide violation(s) found. Commit will be aborted.
remote: Please follow the puppet style guide outlined at:
remote: http://docs.puppetlabs.com/guides/style_guide.html
remote: Error: 1 subhooks failed. Declining push.
remote:
To ssh://git@bitbucket.example.com:7999/pup/control-repo.git
 ! [remote rejected] production -> production (pre-receive hook declined)
error: failed to push some refs to 'ssh://git@bitbucket.example.com:7999/pup/control-repo.git'
```
