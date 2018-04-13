[[_TOC_]]

# WARNING

PhoneTrack **does not work if it's restricted to some groups**. The reason is it's impossible to access public pages of an app (log URLs in our case) because Nextcloud considers the app is disabled when it is accessed without being logged in.

**It has been solved** in [this pull-request](https://github.com/nextcloud/server/pull/8593). Be patient, it will be included in Nextcloud 14.

# Issue with PostgreSQL

As reported here :
https://gitlab.com/eneiluj/phonetrack-oc/issues/82#note_68155878
there are issues when updating PhoneTrack if your Nextcloud instance uses a PostgreSQL database. Solutions are given in the issue thread.

# Install instructions

Put phonetrack directory in Owncloud/Nextcloud apps directory to install.
There are several ways to do that :

### Clone the git repository

```
cd /path/to/owncloud/apps
git clone https://gitlab.com/eneiluj/phonetrack-oc.git phonetrack
```

### Download from https://marketplace.owncloud.com or https://apps.nextcloud.com

Extract phonetrack archive you just downloaded from the website :
```
cd /path/to/owncloud/apps
tar xvf phonetrack-x.x.x.tar.gz