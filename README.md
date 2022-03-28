
pinentry-env
============

This is a pinentry implementation that reads the passphrase from an environment variable.

This script was designed to be able to sign artifacts in Azure pipelines, using an OpenPGP smart
card installed on a on-premises machine.

Usage
-----

First, download and install the pinentry-env file, and make sure that it's got the executable
bit set.

Then, configure the GnuPG agent to use this pinentry interface, by editing or creating the
`~/.gnupg/gpg-agent.conf` file, and inserting the following option:

```
pinentry-program /path/to/pinentry-env
```

Finally, to use it, export an environment variable called `GPG_PASSPHRASE` containing the key's
passphrase, and call the sign command:

```bash
export GPG_PASSPHRASE=CorrectHorseBatteryStaple
gpg --sign l33t-project.tar.gz
```

```bash
export GPG_PASSPHRASE=CorrectHorseBatteryStaple
rpm --addsign l33t-project.rpm
```

Acknowledgements
----------------

Based on `fake-pinentry.sh` by [Daniel Kahn Gillmor](https://github.com/dkg).
