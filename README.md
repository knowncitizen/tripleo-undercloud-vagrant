# tripleo-undercloud-vagrant
A Vagrantfile for quickly firing up a tripleo undercloud with latest repos.

## Pre-requisites

You'll need [vagrant](https://github.com/hashicorp/vagrant) with the [vagrant-libvirt](https://github.com/vagrant-libvirt/vagrant-libvirt) plugin.

## Usage

You might want to take a look at the Vagrant file before you begin to make sure you want the specified network and things like fpaste (you may not!).   After that, just run:
```
vagrant up
```
You can run the vagrant ssh-config to get the relevant ssh-config info:
```
vagrant ssh-config >> ~/.ssh/config
```
Edit the ~/.ssh/config to be the name 'undercloud'. Once you've finished that, you can use sshuttle (which you can find [here](https://github.com/sshuttle/sshuttle)) and run something along the lines of:
```
sshuttle -vr undercloud 0/0
```
You can then access the IP above in ~/.ssh/config as the starting point for the UI, or tie into it via a fork of [TripleO-UI](https://github.com/knowncitizen/tripleo-ui)

Finally, you can do the following and have an undercloud:
```
openstack undercloud install
```

## Other Stuff

The ssh-config is just an example.  It's easier to just generate it.

## Contributing

1. Fork it ( https://github.com/[my-github-username]/tripleo-undercloud-vagrant/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
