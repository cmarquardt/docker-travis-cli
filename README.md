# docker-travis

Dockerized version of the  [Travis Command Line Client](https://github.com/travis-ci/travis.rb).

## Installation

This image is not run manually; instead, use a helper shell script
to execute it. To install the helper script, copy the script `travis` to your `PATH`, e.g.:

```shell
curl https://raw.githubusercontent.com/cmarquardt/docker-travis/master/travis.sh \
  -o ~/bin/travis && \
chmod +x ~/bin/travis
```

## Examples

### Encrypting environment variables
```shell
travis encrypt SECRET=123 -r org/repo
```

### Interactive setup of `.travis.yml`
```shell
travis setup pypi
```

### Validating your `.travis.yml` with travis lint
```shell
travis lint .travis.yml
```

## Usage

```shell
$ travis help
Usage: travis COMMAND ...

Available commands:

	accounts       displays accounts and their subscription status
	branches       displays the most recent build for each branch
	cache          lists or deletes repository caches
	cancel         cancels a job or build
	console        interactive shell
	disable        disables a project
	enable         enables a project
	encrypt        encrypts values for the .travis.yml
	encrypt-file   encrypts a file and adds decryption steps to .travis.yml
	endpoint       displays or changes the API endpoint
	env            show or modify build environment variables
	help           helps you out when in dire need of information
	history        displays a projects build history
	init           generates a .travis.yml and enables the project
	lint           display warnings for a .travis.yml
	login          authenticates against the API and stores the token
	logout         deletes the stored API token
	logs           streams test logs
	monitor        live monitor for what's going on
	open           opens a build or job in the browser
	pubkey         prints out a repository's public key
	raw            makes an (authenticated) API call and prints out the result
	report         generates a report useful for filing issues
	repos          lists repositories the user has certain permissions on
	requests       lists recent requests
	restart        restarts a build or job
	settings       access repository settings
	setup          sets up an addon or deploy target
	show           displays a build or job
	sshkey         checks, updates or deletes an SSH key
	status         checks status of the latest build
	sync           triggers a new sync with GitHub
	token          outputs the secret API token
	version        outputs the client version
	whatsup        lists most recent builds
	whoami         outputs the current user

Run `travis help COMMAND` for more information.
```

## Maintenance

To rebuild the image:

```shell
git clone git://github.com/cmarquardt/travis
make build
```

To publish the image:

```shell
docker login -u <user> -p <password>
make push
```

---

Credits go to [sdt/docker-raspberry-pi-cross-compiler](https://github.com/sdt/docker-raspberry-pi-cross-compiler), who invented the base of the dockerized script, and [jcfr/travis-cli](https://github.com/jcfr/docker-travis-cli), who provided a version of the dockerized Travis CLI client on which this one is based.
