# openshift-puppet-cartridge

An experimental puppet cartridge for OpenShift.  Currently this
downloads facter and puppet, installs them, and attempts to set up
a working puppet config.

See bin/install for the options used to generate puppet.conf

## Suggested usage

* `rhc cartridge add "http://<raw manifest>" -a _your-app-name_`
* Create `~/puppet/environments/production/manifests/site.pp`.
For example:

```
file { 'testfile' :
      path    => '/tmp/testfile',
      ensure  => present,
      mode    => 0640,
      content => 'I am a test file.',
    }
```

* In .openshift/action_hooks/deploy in your app repository, add the following line:

```
puppet apply
```

