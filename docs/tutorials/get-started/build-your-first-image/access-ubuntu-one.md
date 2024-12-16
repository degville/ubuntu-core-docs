(tutorials-get-started-build-your-first-image-access-ubuntu-one)=
# Access Ubuntu One

To use Ubuntu Core, to build and sign an image, or publish a snap, you need an [Ubuntu One](https://login.ubuntu.com/) account.

Ubuntu One is a single sign-on service (SSO) for Ubuntu and its affiliated projects, including [snapcraft.io](https://snapcraft.io), the central resource for all snap-related publishing.

See below for details on how to create an account, login, and retrieve your developer account details.

---

- [1. Create an Ubuntu One account](#heading--create-account)
- [2. Snapcraft credentials](#heading--create-account)
- [3. Retrieve your developer account id](#heading--developer-id)

<h2 id='heading--create-account'>1. Create an Ubuntu One account</h2>

You will need an [Ubuntu One account](https://snapcraft.io/account) with an uploaded public key of a locally generated SSH key pair. 

See [Use Ubuntu One for SSH](/how-to-guides/manage-ubuntu-core/use-ubuntu-one-ssh) for instructions on how to create an account and register an SSH key. With this done,  your Ubuntu One account is ready to use.

You will now need to retrieve your developer account identifier. This is part of your Ubuntu One account and is used to link your account to any Ubuntu Core images you create.

The next steps need to be performed in an existing Ubuntu LTS environment.

<h2 id='heading--snapcraft-credentials'>2. Snapcraft credentials</h2>

Your developer identifier can be retrieved with the [`snapcraft`](https://snapcraft.io/docs/snapcraft-overview) command, the tool that's also used to build and publish snaps. It can be installed by running:

```bash
sudo snap install snapcraft --classic
```

We now need to use `snapcraft` to export your login authentication credentials, and to place them within an environment variable:

```bash
snapcraft export-login credentials.txt
export SNAPCRAFT_STORE_CREDENTIALS=$(cat credentials.txt)
```

You will be asked for your Ubuntu One email address and password, and encouraged to enable two-factor authentication (2FA) if you haven't already done so.

<h2 id='heading--developer-id'>3. Retrieve your developer account ID</h2>

With your authentication in place, the `snapcraft whoami` command will now display your developer identifier after the `id` field:

```bash
$ snapcraft whoami
email: <email-address>
username: <username>
id: xSfWKGdLoQBoQx88
permissions: package_access, package_manage, package_metrics, package_push, package_register, package_release, package_update
channels: no restrictions
expires: 2024-04-17T10:25:13.675Z 
```

In the output above, the example **id** is `xSfWKGdLoQBoQx88` -- we'll use this ID for subsequent examples, but you should obviously use your own ID from now on.
