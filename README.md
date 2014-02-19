# DOCKER + ANSIBLE + VAGRANT Example

## Set up our deployment box
This box will represent a pre-existing remote machine where
we'd like to deploy a new app

### Step 1 - Start our Vagrant VM
This is used to simulate a remote machine for deployment
```bash
vagrant up
```

### Step 2 - Set up our docker container
```bash
vagrant ssh
cd /vagrant/docker_init
docker build -rm -t jbangel/davex .
```

if you have ansible installed
```bash
ansible -i ./dav_inv davex -m git clone fun stuff
```

if you do not have ansible installed, don't fret
```bash
ssh 192.168.15.90 'ansible'
```


