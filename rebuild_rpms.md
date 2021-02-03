## How to rebuild a package from Fedora or EPEL for RHEL, CentOS, SL, ...

First off, there is a lot of good documentation on how to build and rebuild RPM packages. This guide should lead you through rebuilding RPMs quickly. It shall also introduce you to some of the tools packagers use. This guide is not specific to Zabbix; you can rebuild any other package in the same fashion.

If you want to learn more about packaging, you might be interested in:

http://fedoraproject.org/wiki/How_to_create_an_RPM_package
http://wiki.centos.org/HowTos/RebuildSRPM

Why should you choose packaging over "make install"?

Packages make your life easier in many aspects:

You can deploy packages easily on many systems by using a repository

You can install and remove them in a clean way

Dependencies on other packages are tracked for you

There's a policy for updating configuration files

If you're using somebody else's packages:

Somebody else is doing most of the work for you

Package maintainers patch out major bugs, adapt the software to your distribution and usually keep the packages up to date. Many of them invest a lot of time in doing so. You can profit from their efforts. Still you can download and manipulate their work to fit your personal needs. So-called source RPMs contain all necessary sources and a spec file, which is the building plan for the resulting RPM packages.

On top of all that, you can build for different versions of your distribution or architectures on just one system and without cluttering your system with development packages, if you follow this guide.

Where do I find source RPMs?

Fedora maintains a repository called EPEL -- Extra Packages for Enterprise Linux. This repository offers a lot of additional packages. The EPEL policy is never to overwrite packages from RHEL. Also, the only updates allowed to EPEL packages are bug-fixes. You therefore won't see the brand new versions later on -- at least not with the same package name.

Say you're on RHEL 5 and seeking for the brand new version of Zabbix. Looking around on Fedora's build service Koji, you discover there is an up-to-date package. Sadly it is in EPEL 6 -- not 5. If you have this kind of problem, this guide is for you.

Please notice: Not all builds in Koji are actually shipped. Besides that, there is an incubation time, where these updates are in a testing repository. You can check the status of updates in Bodhi.

This guide addresses the following scenarios

You want packages for RHEL/CentOS/SL 5.x and you see exactly what you want, but in EPEL 6

You want packages for RHEL/CentOS/SL 5 or 6 and you see exactly what you want, but in Fedora

You're on RHEL/CentOS/SL and there is a package in newest EPEL or Fedora, but but you want an even newer version packaged
What you're searching for is in EPEL/Fedora, but you want to adapt the packages to your needs
Pre-requisites

Don't install any devel packages you need for your package
Activate the EPEL repository, if you haven't done so already.

     rpm -i http://download.fedoraproject.org/pub/epel/5/i386/epel-release-5-4.noarch.rpm

or

     rpm -i http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-5.noarch.rpm

This is a "noarch" package, which indicates it is not architecure dependent. It therefore doesnt matter if you install the package from the i386, x86_64 or any other directory.

Install fedora-packager

     yum install fedora-packager

This will install amongst others: createrepo, mock, rpmlint, rpmdevtools and rpm-build. There seem to be a couple of repositories that offer the Mock package. If you're using a different version than the one from EPEL, things might behave different or not work. In that case, try to disable these packages for all other repositories, using "exclude". See man yum.conf 5 for details.

Create a user called "makerpm" or something, add it to the group mock. Run rpmdev-setuptree while logged in as this user.

```
   useradd makerpm -G mock
   passwd makerpm
   su - makerpm
   rpmdev-setuptree
```

http://fedoraproject.org/wiki/Using_Mock_to_test_package_builds#Using_Mock_outside_your_git_sandbox

http://fedoraproject.org/wiki/How_to_create_an_RPM_package#Setting_up_your_system_and_account

1. You want version 5 packages, desired package is in EPEL 6

Let's say you see the brand new version of Zabbix in EPEL 6:

http://koji.fedoraproject.org/koji/packageinfo?packageID=4278

You could try to just download the RPMs and install them. But Yum would likely refuse to do so, because some dependency requirements are not met by your version 5 distribution. To work around this, rebuild the source RPM package. A source RPM contains a "building plan", upstream's sources and additional sources, as well as patches to the sources.

Download the SRPM (something.src.rpm) from Koji

The checksum algorithm for RPMs changed between RHEL 5 and 6. Thus Mock would not rebuild RPMs from EPEL 6 for a version 5 distribution. Run as user makerpm:

     rpm --nomd5 -ih something.src.rpm

Ignore warnings about users and groups not existing!

     rpmbuild -bs --nodeps ~/rpmbuild/SPECS/something.spec

If you set up mock on a 6 system do instead:

    rpmbuild-md5 -bs ~/rpmbuild/SPECS/something.spec

This step created a new SRPM in ~/rpmbuild/SRPMS

Run Mock and feed it with this SRPM:

     mock --rebuild ~/rpmbuild/SRPMS/mysrpm.src.rpm

This will build packages for your distribution version and architecture. If you want something different, add "-r my_distri_configuration". Please see /etc/mock for possible configuration names. Don't add the ".cfg". For details see:

   http://fedoraproject.org/wiki/Using_Mock_to_test_package_builds

Hopefully pick up the finished RPM packages; you're done! Mock tells you where to find them, when it is done.
If you want to run your own repository, acquaint yourself with createrepo. If you don't sign your packages, install with "yum --nogpgcheck ..." or use "gpgcheck = 0" in your yum repo file. Be aware that repository metadata also uses different kinds of checksums in 5 and 6. Also notice, 5 packages can only be signed with DSA keys, because of a weakness in 5's rpm.

2. You want packages for version 5 or 6, desired package is in Fedora

If you're building packages for version 5, the steps are exactly as described above. If you're building packages for version 6, you can go straight to mock, after you downloaded the SRPM.

Be aware of the possible pitfalls as compared to rebuilds from EPEL:

The package might not build for you at all
In order to build, it might need updated dependencies.
I discourage you on doing that, if these are dependencies that originally ship with RHEL.
In order to build, it might need additional packages
As they are not present in your original or EPEL packages, you can try to rebuild these as well. Again, same procedure applies, same problems exist.

To work around any of the above problems, you might want to browse around Koji for slightly older versions.

3. Package an even newer version

If the package is outdated in the newest version of Fedora, consider to file a bug against Fedora, if nobody has done so yet. Most packagers will react to such a ticket and will update the package. This relieves you from doing so and you can just rebuild what they deliver.

If the packager does not react or you can't wait, see below.

4. Package a newer version or adapt the packages to your needs

If you need specific build flags or need to change something else, install the SRPM using rpm, as described in 1). Also if you want to package a newer version, that has not been packaged yet, rather base your work on what is there already. You can also try to send your changes to the Fedora packager, if he hasn't updated the package yet, although a new release is out for some time.

All necessary files are installed in the rpmbuild directory, located in makerpm's home directory. Now download new sources, update or change the spec file, add your custom configuration to install or do whatever else you wish.

I heavily suggest to change the release number and leave a proper changelog entry in the spec file. You might also want to track your changes using a version control system. If you want to avoid that official packages collide with your private ones, I propose to use the Epoch tag. The epoch is the most significant part of the package version. EPEL, for instance, normally doesn't use epoch. Hence "Epoch:1" will usually be enough to always regard your packages newer.

For version 5 packages, run as user makerpm:

```
 rpmbuild-md5 -bs ~/rpmbuild/SPECS/myspecfile.spec
 mock -r my_version_5_config --rebuild my_source_rpm.src.rpm
```

See 1. for explanation on "my_version_5_config".

For version 6 packages, run as user makerpm:

```
 rpmbuild -bs ~/rpmbuild/SPECS/myspecfile.spec
 mock -r my_version_6_config --rebuild my_source_rpm.src.rpm
```

See 1. for explanation on "my_version_6_config".

Volker Fröhlich, 2011

volker27<at>gmx.at

volter on freenode.net IRC

I'm happy to receive your comments, suggestions and corrections.
