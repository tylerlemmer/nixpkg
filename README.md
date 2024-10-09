# nixpkg
nix configs for ubuntu

Declare nix packages for ubuntu and nix on wsl.

Start with the installation found here: Multi-user installation (recommended)
https://nixos.org/download/

Apt was used to install curl:

sudo apt update
sudo apt upgrade
y
sudo apt install curl

<pre><font color="#26A269"><b>yupper@l7410</b></font>:<font color="#12488B"><b>~</b></font>$ sh &lt;(curl -L https://nixos.org/nix/install) --daemon
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100  4267  100  4267    0     0   5220      0 --:--:-- --:--:-- --:--:--  5220
downloading Nix 2.24.9 binary tarball for x86_64-linux from &apos;https://releases.nixos.org/nix/nix-2.24.9/nix-2.24.9-x86_64-linux.tar.xz&apos; to &apos;/tmp/nix-binary-tarball-unpack.9LHXGA8UNc&apos;...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 22.5M  100 22.5M    0     0  10.1M      0  0:00:02  0:00:02 --:--:-- 10.1M
Note: a multi-user installation is possible. See https://nixos.org/manual/nix/stable/installation/installing-binary.html#multi-user-installation
<font color="#C01C28"><b>Switching to the Multi-user Installer</b></font>
<font color="#26A269">Welcome to the Multi-User Nix Installation</font>

This installation tool will set up your computer with the Nix package
manager. This will happen in a few stages:

1. Make sure your computer doesn&apos;t already have Nix. If it does, I
   will show you instructions on how to clean up your old install.

2. Show you what I am going to install and where. Then I will ask
   if you are ready to continue.

3. Create the system users <font color="#12488B">(uids [30001..30032])</font> and groups <font color="#12488B">(gid 30000)</font>
   that the Nix daemon uses to run builds. To create system users
   in a different range, exit and run this tool again with
   NIX_FIRST_BUILD_UID set.

4. Perform the basic installation of the Nix files daemon.

5. Configure your shell to import special Nix Profile files, so you
   can use Nix.

6. Start the Nix daemon.

<font color="#26A269"><u style="text-decoration-style:single">Would you like to see a more detailed list of what I will do?</u></font>
[y/n] ^C
<font color="#12488B">---- oh no! --------------------------------------------------------------------</font>
<font color="#C01C28">Oh no, something went wrong. If you can take all the output and open</font>
<font color="#C01C28">an issue, we&apos;d love to fix the problem so nobody else has this issue.</font>

<font color="#C01C28">:(</font>

<font color="#C01C28">We&apos;d love to help if you need it.</font>

<font color="#C01C28">You can open an issue at</font>
<font color="#C01C28">https://github.com/NixOS/nix/issues/new?labels=installer&amp;template=installer.md</font>

<font color="#C01C28">Or get in touch with the community: https://nixos.org/community</font>
<font color="#26A269"><b>yupper@l7410</b></font>:<font color="#12488B"><b>~</b></font>$ ^C
<font color="#26A269"><b>yupper@l7410</b></font>:<font color="#12488B"><b>~</b></font>$ sh &lt;(curl -L https://nixos.org/nix/install) --daemon
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100  4267  100  4267    0     0   9130      0 --:--:-- --:--:-- --:--:--  9130
downloading Nix 2.24.9 binary tarball for x86_64-linux from &apos;https://releases.nixos.org/nix/nix-2.24.9/nix-2.24.9-x86_64-linux.tar.xz&apos; to &apos;/tmp/nix-binary-tarball-unpack.IADrfleLWY&apos;...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 22.5M  100 22.5M    0     0  10.2M      0  0:00:02  0:00:02 --:--:-- 10.2M
Note: a multi-user installation is possible. See https://nixos.org/manual/nix/stable/installation/installing-binary.html#multi-user-installation
<font color="#C01C28"><b>Switching to the Multi-user Installer</b></font>
<font color="#26A269">Welcome to the Multi-User Nix Installation</font>

This installation tool will set up your computer with the Nix package
manager. This will happen in a few stages:

1. Make sure your computer doesn&apos;t already have Nix. If it does, I
   will show you instructions on how to clean up your old install.

2. Show you what I am going to install and where. Then I will ask
   if you are ready to continue.

3. Create the system users <font color="#12488B">(uids [30001..30032])</font> and groups <font color="#12488B">(gid 30000)</font>
   that the Nix daemon uses to run builds. To create system users
   in a different range, exit and run this tool again with
   NIX_FIRST_BUILD_UID set.

4. Perform the basic installation of the Nix files daemon.

5. Configure your shell to import special Nix Profile files, so you
   can use Nix.

6. Start the Nix daemon.

<font color="#26A269"><u style="text-decoration-style:single">Would you like to see a more detailed list of what I will do?</u></font>
[y/n] y


I will:

 - make sure your computer doesn&apos;t already have Nix files
   (if it does, I will tell you how to clean them up.)
 - create local users (see the list above for the users I&apos;ll make)
 - create a local group (nixbld)
 - install Nix in /nix
 - create a configuration file in /etc/nix
 - set up the &quot;default profile&quot; by creating some Nix-related files in
   /root
 - back up /etc/bash.bashrc to /etc/bash.bashrc.backup-before-nix
 - update /etc/bash.bashrc to include some Nix configuration
 - load and start a service (at /etc/systemd/system/nix-daemon.service
   and /etc/systemd/system/nix-daemon.socket) for nix-daemon

<font color="#26A269"><u style="text-decoration-style:single">Ready to continue?</u></font>
[y/n] ^[[A^[[B^[[A^[[Ay
<font color="#C01C28">Sorry, I didn&apos;t understand. I can only understand answers of y or n</font>
[y/n] y


<font color="#12488B">---- let&apos;s talk about sudo -----------------------------------------------------</font>
This script is going to call sudo a lot. Every time I do, it&apos;ll
output exactly what it&apos;ll do, and why.

Just like this:

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo echo

to demonstrate how our sudo prompts look


This might look scary, but everything can be undone by running just a
few commands. I used to ask you to confirm each time sudo ran, but it
was too many times. Instead, I&apos;ll just ask you this one time:

<font color="#26A269"><u style="text-decoration-style:single">Can I use sudo?</u></font>
[y/n] y

<font color="#26A269">Yay! Thanks! Let&apos;s get going!</font>

<font color="#26A269">~~&gt; Checking for artifacts of previous installs</font>
Before I try to install, I&apos;ll check for signs Nix already is or has
been installed on this system.

<font color="#12488B">---- Nix config report ---------------------------------------------------------</font>
<b>        Temp Dir</b>:	/tmp/tmp.Dsm63uolAW
<b>        Nix Root</b>:	/nix
<b>     Build Users</b>:	32
<b>  Build Group ID</b>:	30000
<b>Build Group Name</b>:	nixbld

<font color="#12488B"><u style="text-decoration-style:single">build users:</u></font>
<b>    Username</b>:	UID
<b>     nixbld1</b>:	30001
<b>     nixbld2</b>:	30002
<b>     nixbld3</b>:	30003
<b>     nixbld4</b>:	30004
<b>     nixbld5</b>:	30005
<b>     nixbld6</b>:	30006
<b>     nixbld7</b>:	30007
<b>     nixbld8</b>:	30008
<b>     nixbld9</b>:	30009
<b>     nixbld10</b>:	30010
<b>     nixbld11</b>:	30011
<b>     nixbld12</b>:	30012
<b>     nixbld13</b>:	30013
<b>     nixbld14</b>:	30014
<b>     nixbld15</b>:	30015
<b>     nixbld16</b>:	30016
<b>     nixbld17</b>:	30017
<b>     nixbld18</b>:	30018
<b>     nixbld19</b>:	30019
<b>     nixbld20</b>:	30020
<b>     nixbld21</b>:	30021
<b>     nixbld22</b>:	30022
<b>     nixbld23</b>:	30023
<b>     nixbld24</b>:	30024
<b>     nixbld25</b>:	30025
<b>     nixbld26</b>:	30026
<b>     nixbld27</b>:	30027
<b>     nixbld28</b>:	30028
<b>     nixbld29</b>:	30029
<b>     nixbld30</b>:	30030
<b>     nixbld31</b>:	30031
<b>     nixbld32</b>:	30032

<font color="#26A269"><u style="text-decoration-style:single">Ready to continue?</u></font>
[y/n] y


<font color="#26A269">~~&gt; Setting up the build group nixbld</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo groupadd -g 30000 --system nixbld

Create the Nix build group, nixbld

[sudo] password for yupper: 
<b>            Created</b>:	Yes

<font color="#26A269">~~&gt; Setting up the build user nixbld1</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 1 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30001 --password ! nixbld1

Creating the Nix build user, nixbld1

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 1
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld2</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 2 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30002 --password ! nixbld2

Creating the Nix build user, nixbld2

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 2
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld3</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 3 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30003 --password ! nixbld3

Creating the Nix build user, nixbld3

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 3
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld4</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 4 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30004 --password ! nixbld4

Creating the Nix build user, nixbld4

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 4
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld5</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 5 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30005 --password ! nixbld5

Creating the Nix build user, nixbld5

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 5
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld6</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 6 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30006 --password ! nixbld6

Creating the Nix build user, nixbld6

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 6
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld7</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 7 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30007 --password ! nixbld7

Creating the Nix build user, nixbld7

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 7
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld8</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 8 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30008 --password ! nixbld8

Creating the Nix build user, nixbld8

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 8
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld9</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 9 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30009 --password ! nixbld9

Creating the Nix build user, nixbld9

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 9
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld10</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 10 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30010 --password ! nixbld10

Creating the Nix build user, nixbld10

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 10
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld11</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 11 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30011 --password ! nixbld11

Creating the Nix build user, nixbld11

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 11
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld12</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 12 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30012 --password ! nixbld12

Creating the Nix build user, nixbld12

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 12
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld13</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 13 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30013 --password ! nixbld13

Creating the Nix build user, nixbld13

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 13
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld14</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 14 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30014 --password ! nixbld14

Creating the Nix build user, nixbld14

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 14
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld15</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 15 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30015 --password ! nixbld15

Creating the Nix build user, nixbld15

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 15
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld16</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 16 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30016 --password ! nixbld16

Creating the Nix build user, nixbld16

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 16
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld17</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 17 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30017 --password ! nixbld17

Creating the Nix build user, nixbld17

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 17
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld18</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 18 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30018 --password ! nixbld18

Creating the Nix build user, nixbld18

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 18
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld19</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 19 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30019 --password ! nixbld19

Creating the Nix build user, nixbld19

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 19
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld20</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 20 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30020 --password ! nixbld20

Creating the Nix build user, nixbld20

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 20
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld21</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 21 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30021 --password ! nixbld21

Creating the Nix build user, nixbld21

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 21
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld22</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 22 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30022 --password ! nixbld22

Creating the Nix build user, nixbld22

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 22
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld23</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 23 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30023 --password ! nixbld23

Creating the Nix build user, nixbld23

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 23
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld24</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 24 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30024 --password ! nixbld24

Creating the Nix build user, nixbld24

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 24
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld25</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 25 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30025 --password ! nixbld25

Creating the Nix build user, nixbld25

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 25
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld26</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 26 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30026 --password ! nixbld26

Creating the Nix build user, nixbld26

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 26
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld27</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 27 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30027 --password ! nixbld27

Creating the Nix build user, nixbld27

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 27
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld28</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 28 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30028 --password ! nixbld28

Creating the Nix build user, nixbld28

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 28
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld29</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 29 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30029 --password ! nixbld29

Creating the Nix build user, nixbld29

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 29
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld30</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 30 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30030 --password ! nixbld30

Creating the Nix build user, nixbld30

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 30
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld31</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 31 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30031 --password ! nixbld31

Creating the Nix build user, nixbld31

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 31
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the build user nixbld32</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo useradd --home-dir /var/empty --comment Nix build user 32 --gid 30000 --groups nixbld --no-user-group --system --shell /sbin/nologin --uid 30032 --password ! nixbld32

Creating the Nix build user, nixbld32

<b>           Created</b>:	Yes
<b>            Hidden</b>:	Yes
<b>    Home Directory</b>:	/var/empty
<b>              Note</b>:	Nix build user 32
<b>   Logins Disabled</b>:	Yes
<b>  Member of nixbld</b>:	Yes
<b>    PrimaryGroupID</b>:	30000

<font color="#26A269">~~&gt; Setting up the basic directory structure</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo install -dv -m 0755 /nix /nix/var /nix/var/log /nix/var/log/nix /nix/var/log/nix/drvs /nix/var/nix /nix/var/nix/db /nix/var/nix/gcroots /nix/var/nix/profiles /nix/var/nix/temproots /nix/var/nix/userpool /nix/var/nix/daemon-socket /nix/var/nix/gcroots/per-user /nix/var/nix/profiles/per-user

to make the basic directory structure of Nix (part 1)

install: creating directory &apos;/nix&apos;
install: creating directory &apos;/nix/var&apos;
install: creating directory &apos;/nix/var/log&apos;
install: creating directory &apos;/nix/var/log/nix&apos;
install: creating directory &apos;/nix/var/log/nix/drvs&apos;
install: creating directory &apos;/nix/var/nix&apos;
install: creating directory &apos;/nix/var/nix/db&apos;
install: creating directory &apos;/nix/var/nix/gcroots&apos;
install: creating directory &apos;/nix/var/nix/profiles&apos;
install: creating directory &apos;/nix/var/nix/temproots&apos;
install: creating directory &apos;/nix/var/nix/userpool&apos;
install: creating directory &apos;/nix/var/nix/daemon-socket&apos;
install: creating directory &apos;/nix/var/nix/gcroots/per-user&apos;
install: creating directory &apos;/nix/var/nix/profiles/per-user&apos;

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo install -dv -g nixbld -m 1775 /nix/store

to make the basic directory structure of Nix (part 2)

install: creating directory &apos;/nix/store&apos;

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo install -dv -m 0555 /etc/nix

to place the default nix daemon configuration (part 1)

install: creating directory &apos;/etc/nix&apos;

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo install -m 0664 /tmp/tmp.Dsm63uolAW/.nix-channels /root/.nix-channels

to set up the default system channel (part 1)


<font color="#26A269">~~&gt; Installing Nix</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo cp -RPp ./store/0wb2jfh9zcdhh2maw76vrcd69yn56hw2-aws-c-sdkutils-0.1.16 ./store/0wq0r67l1lixwiwb7zyjbpl3yff5nbxw-boehm-gc-8.2.6 ./store/19avl2s0rd4whz3b0n118qdrv6yr3b0g-xgcc-13.2.0-libgcc ./store/2k9k3q1vk8z6w7743k6nb22vnb05xv06-zlib-1.3.1 ./store/2nhrwv91g6ycpyxvhmvc0xs8p92wp4bk-nix-2.24.9 ./store/2vdxsvrjrf1bgznbb9wga1rshpxc658a-publicsuffix-list-0-unstable-2024-01-07 ./store/39jg2qg6jlfm4hdc8j61d09skxg4gfw0-acl-2.3.2 ./store/40yjzm7r5ki59kkk9423dnwbm86x7pyd-gcc-13.2.0-lib ./store/503h8rdwzj12dh0fs1b6y643qm26vqsb-libunistring-1.1 ./store/5d4a4am9gb7ia79xfjcdbf2y3b9kwknn-aws-c-event-stream-0.4.2 ./store/5xvdvbb7vzyazmhw57yhwwch8kqwjfyk-aws-c-http-0.8.1 ./store/65ysp6n926dmcxdsg88q4qkw1kid7dih-attr-2.5.2 ./store/852a51xd3m7jyzifqimxc3jf3w2ipc4k-nss-cacert-3.101 ./store/86b4h0x1i310gglrsjrk093l0g2h26pr-aws-sdk-cpp-1.11.318 ./store/87848rvrg5c7jmplpi0iapvbxyj9kfid-glibc-2.39-52 ./store/8c9vyhad2gxlg4clvaa3zlikv7lsym3s-libsodium-1.0.19 ./store/8ivnsqp0wb8pna7rm31csdcn5aykdkqh-s2n-tls-1.4.12 ./store/96dj8i2gxxn31nw84r94h7bbfbg46rkw-pcre-8.45 ./store/9g700djj7aqgr3fqq5ji9m8w3n5ip75s-xz-5.4.7 ./store/ayndm66jniwbm76kprjjng06r4b7ypbw-keyutils-1.6.3-lib ./store/b5248mzca3qjhjvck1vw3n6gg5mdhkz8-aws-c-common-0.9.17 ./store/bdk3lnfjx46vsh5php2wbxsr9mriyhqb-aws-c-s3-0.5.7 ./store/by2v5cgvm6kkjjfv52fz7vajwgmcfdga-brotli-1.1.0-lib ./store/c46xzl45zg6225nxy780ccm5bzm9bdc4-aws-crt-cpp-0.26.8 ./store/ddzqsmrcpciq7rm4p70ynj3hi07w88kz-libxml2-2.12.7 ./store/dqrip0sx49kz9l6p8smq09aghas49s3b-gcc-13.2.0-libgcc ./store/dyxmqfpx08c2rhxg5kc83qa0qdxhzhfk-aws-c-cal-0.6.12 ./store/f6afb4jw9g5f94ixw0jn6cl0ah4liy35-sqlite-3.45.3 ./store/g0gx36d1l273mzhnz7jmq5vvjf6n9r70-bzip2-1.0.8 ./store/g45c2banpvki32fjydbx3wclgcphmsbs-libpsl-0.21.5 ./store/isqwk2fj3d87ykqkhgr1513jqlrkymr6-lowdown-1.1.0-lib ./store/j8qdcfmjnlqlxk14mh59vcwr6hbznj92-boost-1.81.0 ./store/kcc6cnkqm8if32y6hwh9ixpwxba15hkq-nghttp2-1.61.0-lib ./store/kw6idhj5b1pmwjg7rnyvrlhg5ffrn1vs-curl-8.7.1 ./store/m5lk8pdk0sz0pkf3kjzk0j2b7gargzzx-aws-c-compression-0.2.18 ./store/mccadsxm3sgrcx2z0b9c8d5wgnlg7a3z-libarchive-3.7.4-lib ./store/mldkgahcv5kg2kv19dc8zqmz5y702k01-aws-c-io-0.14.7 ./store/p66hqwsh90q1xdb6ss31105rr11s4z9v-busybox-static-x86_64-unknown-linux-musl-1.36.1 ./store/p8pfm2w0sapcyizn9rkgdpllywq05x5n-libseccomp-2.5.5-lib ./store/p95ba37n695180m4vjp4mn3j8vd156jr-libcpuid-0.6.5 ./store/q46sbq9pgf58xb8zx5vlkbv96kidglxc-openssl-3.0.14 ./store/qcwlfkj0yggkfvv43y0bv7wyb35w1dh0-editline-1.17.1 ./store/rpj7hvnzrm4kh45bllm7fgncwmshlhiq-aws-c-mqtt-0.10.4 ./store/wckka8fxv4h5hp74cbkhaw3fw7kbvcs1-bash-5.2p26 ./store/xhd47fvyzk5gds3d6bnnvhfpqd9hrsvp-aws-c-auth-0.7.18 ./store/ya4arqpf6vwbq4msi449314kqbhdb4l4-libidn2-2.3.7 ./store/ydmbcr9ca5sdhvlx8icwvj454xvp6dd8-aws-checksums-0.1.18 ./store/yh9n3w67ivhxkzx9m58cswbaf8nag436-zstd-1.5.6 ./store/z5736fyn17s2mqql62rcznmj5yk5yx15-libkrb5-1.21.3 ./store/zg49hmjdvmmcak7k7rwvlpnnnz02ljhs-libgit2-20240516095848-lib ./store/zmczdj9cz73g8vfrqkv2hh5fv9achs7v-libssh2-1.11.0 /nix/store/

to copy the basic Nix files to the new store at /nix/store


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo chmod -R ugo-w /nix/store/

to make the new store non-writable at /nix/store

      Alright! We have our first nix at /nix/store/2nhrwv91g6ycpyxvhmvc0xs8p92wp4bk-nix-2.24.9

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo HOME=/root /nix/store/2nhrwv91g6ycpyxvhmvc0xs8p92wp4bk-nix-2.24.9/bin/nix-store --load-db

to load data for the first time in to the Nix Database

      Just finished getting the nix database ready.

<font color="#26A269">~~&gt; Setting up shell profiles: /etc/bashrc /etc/profile.d/nix.sh /etc/zshrc /etc/bash.bashrc /etc/zsh/zshrc</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo touch /etc/bashrc

to create a stub /etc/bashrc which will be updated


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo tee -a /etc/bashrc

extend your /etc/bashrc with nix-daemon settings


# Nix
if [ -e &apos;/nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh&apos; ]; then
  . &apos;/nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh&apos;
fi
# End Nix


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo touch /etc/profile.d/nix.sh

to create a stub /etc/profile.d/nix.sh which will be updated


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo tee -a /etc/profile.d/nix.sh

extend your /etc/profile.d/nix.sh with nix-daemon settings


# Nix
if [ -e &apos;/nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh&apos; ]; then
  . &apos;/nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh&apos;
fi
# End Nix


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo touch /etc/zshrc

to create a stub /etc/zshrc which will be updated


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo tee -a /etc/zshrc

extend your /etc/zshrc with nix-daemon settings


# Nix
if [ -e &apos;/nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh&apos; ]; then
  . &apos;/nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh&apos;
fi
# End Nix


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo cp /etc/bash.bashrc /etc/bash.bashrc.backup-before-nix

to back up your current /etc/bash.bashrc to /etc/bash.bashrc.backup-before-nix


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo tee -a /etc/bash.bashrc

extend your /etc/bash.bashrc with nix-daemon settings


# Nix
if [ -e &apos;/nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh&apos; ]; then
  . &apos;/nix/var/nix/profiles/default/etc/profile.d/nix-daemon.sh&apos;
fi
# End Nix


<font color="#26A269">~~&gt; Setting up shell profiles for Fish with conf.d/nix.fish inside /etc/fish /usr/local/etc/fish /opt/homebrew/etc/fish /opt/local/etc/fish</font>

<font color="#26A269">~~&gt; Setting up the default profile</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo HOME=/root /nix/store/2nhrwv91g6ycpyxvhmvc0xs8p92wp4bk-nix-2.24.9/bin/nix-env -i /nix/store/2nhrwv91g6ycpyxvhmvc0xs8p92wp4bk-nix-2.24.9

to install a bootstrapping Nix in to the default profile

installing &apos;nix-2.24.9&apos;
building &apos;/nix/store/l9ab6qm37vw0g8vblfzrj387khq6qql1-user-environment.drv&apos;...

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo HOME=/root /nix/store/2nhrwv91g6ycpyxvhmvc0xs8p92wp4bk-nix-2.24.9/bin/nix-env -i /nix/store/852a51xd3m7jyzifqimxc3jf3w2ipc4k-nss-cacert-3.101

to install a bootstrapping SSL certificate just for Nix in to the default profile

installing &apos;nss-cacert-3.101&apos;
building &apos;/nix/store/zlycwkfk8znkrvqfsjwhlmk85q6lczv3-user-environment.drv&apos;...

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo HOME=/root NIX_SSL_CERT_FILE=/nix/var/nix/profiles/default/etc/ssl/certs/ca-bundle.crt /nix/store/2nhrwv91g6ycpyxvhmvc0xs8p92wp4bk-nix-2.24.9/bin/nix-channel --update nixpkgs

to update the default channel in the default profile

unpacking 1 channels...

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo install -m 0664 /tmp/tmp.Dsm63uolAW/nix.conf /etc/nix/nix.conf

to place the default nix daemon configuration (part 2)


<font color="#26A269">~~&gt; Setting up the nix-daemon systemd service</font>

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo ln -sfn /nix/var/nix/profiles/default/lib/tmpfiles.d/nix-daemon.conf /etc/tmpfiles.d/nix-daemon.conf

to create the nix-daemon tmpfiles config


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo systemd-tmpfiles --create --prefix=/nix/var/nix

to run systemd-tmpfiles once to pick that path up


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo systemctl link /nix/var/nix/profiles/default/lib/systemd/system/nix-daemon.service

to set up the nix-daemon service

Created symlink /etc/systemd/system/nix-daemon.service → /nix/var/nix/profiles/default/lib/systemd/system/nix-daemon.service.

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo systemctl enable /nix/var/nix/profiles/default/lib/systemd/system/nix-daemon.socket

to set up the nix-daemon socket service

Created symlink /etc/systemd/system/sockets.target.wants/nix-daemon.socket → /nix/var/nix/profiles/default/lib/systemd/system/nix-daemon.socket.
Created symlink /etc/systemd/system/nix-daemon.socket → /nix/var/nix/profiles/default/lib/systemd/system/nix-daemon.socket.

<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo systemctl daemon-reload

to load the systemd unit for nix-daemon


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo systemctl start nix-daemon.socket

to start the nix-daemon.socket


<font color="#12488B">---- sudo execution ------------------------------------------------------------</font>
I am executing:

    $ sudo systemctl restart nix-daemon.service

to start the nix-daemon.service

<font color="#26A269">Alright! We&apos;re done!</font>
Try it! Open a new terminal, and type:

  $ nix-shell -p nix-info --run &quot;nix-info -m&quot;

Thank you for using this installer. If you have any feedback or need
help, don&apos;t hesitate:

You can open an issue at
https://github.com/NixOS/nix/issues/new?labels=installer&amp;template=installer.md

Or get in touch with the community: https://nixos.org/community

<font color="#12488B">---- Reminders -----------------------------------------------------------------</font>
<font color="#12488B">[ 1 ]</font>
Nix won&apos;t work in active shell sessions until you restart them.

<font color="#26A269"><b>yupper@l7410</b></font>:<font color="#12488B"><b>~</b></font>$ sh &lt;(curl -L https://nixos.org/nix/install) --daemon


</pre>
