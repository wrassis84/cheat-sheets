|   |   |
|---|---|
| **`yum help`** | Show **`yum`** subcommands and options |
| **`yum list available`** | List all available packages |
| **`yum list installed`** | List all installed packages  |
| **`yum list all`** | List installed and available packages  |
| **`yum list kernel`** | List installed and available kernel packages  |
| **`yum info vsftpd`** | List info about vsftpd package  |
| **`yum deplist nfs-utils`** | List dependencies and packages providing them |
| **`yum provides "*bin/top"`** | Show package that contains top command |
| **`yum search samba`** | Show package containing README.top file |
| **`yum updateinfo security`** | Find packages with samba in name or description |
| **`yum grouplist`** | Get info on available security updates |
| **`yum groupinfo "Web Server"`** | List packages in Web Server group |
| **`check-update`** | Query repositories for available package updates |
| **`yum repolist`** | Display enabled software repositories |
| **`yum repoinfo rhel-7-server-rpms`** | See info on rhel-7-server-rpms repo |
| **`yum repo-pkgs my-rpms list`** | List packages from my-rpms repo |
| **`yum repo-pkgs my-rpms install`** | Install all packages from my-rpms repo |
| **`yum repo-pkgs my-rpms remove`** | Remove all packages from my-rpms repo |
| **`yum makecache`** | Download yum repository data to cache |
| **`yum check`** | Check the local RPM database for problems |
| **`yum history list`** | List all yum install, update and erase actions |
| **`yum history info 3`** | Show details of yum transaction 3 |
| **`yum history undo 3`** | Undo the yum action from transaction 3 |
| **`yum history redo 3`** | Redo the undone yum action from transaction 3 |
| **`yum clean packages`** | Delete packages saved in cache |
| **`yum clean all`** | Clean out all packages and meta data from cache |
| **`yum fssnapshot`** | List LVM stapshots (helps roll back after package updates) |
| **`yum fs`** | Act on filesystem (prevent doc or lang file install on minimal systems) |
| **`yum fs filters`** | List enabled filesystem filters |
| **`yum fs documentation`** | Filters all docs from being installed (careful!) |
| **`yum install vsftpd`** | Install the vsftpd package |
| **`yum update`** | Update all packages with available updates |
| **`yum update httpd`** | Update the httpd package (if available) |
| **`yum update --security`** | Apply security-related package updates |
| **`yum update-to`** | Update one or all packages to a particular version |
| **`yum upgrade`** | Update packages taking obsoletes into account |
| **`yum localinstall package-1-1.i686.rpm`** | Install package from local directory |
| **`yum localinstall http://myrepo/pkg-1-1.i686.rpm`** | Install package from FTP site |
| **`yum downgrade httpd-13.9...`** | Downgrade the httpd package to an earlier version |
| **`yum reinstall util-linux`** | Reinstall util-linux (to replace any deleted files) |
| **`yum swap ftp lftp`** | Remove ftp package and install lftp package |
| **`yum remove vsftpd`** | Remove the vsftpd package and dependencies |
| **`yum erase vsftpd`** | Remove the vsftpd package and dependencies |
| **`yum autoremove httpd`** | Remove httpd and other unneeded packages |
| **`yum groupinstall "Web server"`** | Install Web Server packages |
| **`yum langavailable`** | List all available languages |
| **`yum langinfo es`** | List packages associated with Spanish language |
| **`yum langinstall es`** | Install packages associated with Spanish language|
| **`yum langlist`** | List languages that are installed |
| **`yum langremove es`** | Remove packages associated with Spanish language |
|**install the yum-utils package**|
| **`yum find-repos-of-install`** | Find which repository a package comes from |
| **`yum needs-restarting`** | Find processes that have been updated and need to restart |
| **`yum repoclosure`** | Get unmet dependency list from repositories |
| **`yum repoquery --requires --resolve bash`** | Show dependent packages |
| **`yum reposync -r rhel-atomic-host-beta-rpms`** | Get packages from repo |
| **`yum repotrack`** | Download a package and all its dependencies |
| **`yum show-installed`** | List installed RPM packages and statistics |
| **`yum verifytree`** | Check the local yum repository for consistency |
| **`yum-complete-transaction`** | Try to complete yum transactions that didn’t finish |
| **`yumdb`** | Check or change the yum database |
| **`yumdownloader`** | Download a package from a repo to current directory |
| **`-y`** |  | Assume yes if prompted |
| **`--assumeno`** |  | Assume no if prompted |
| **`-q`** |  | Produce no output |
| **`-v`** |  | Produce extra debugging output |
| **`--noplugins`** |  | Run command without loading any yum plugins |
| **`--disableplugin=`** |  | Disable a particular plugin for single command **`yum --disableplugin=langpacks info vsftpd** |
| **`--enableplugin=`** |  | Enable a plugin that is installed, but currently disabled **`yum --enableplugin=ps ps ** |
Show packages tied to running processes

| **`--enablerepo= Enable currently disabled repo for a single 
command (wildcards okay)
yum install docker \
 --enablerepo=rhel-7-server-extras-rpm

| **`--disablerepo= Disable currently enabled repo for a single 
command (wildcards okay)
yum list available --disablerepo=epel

| **`--downloadonly Download to /var/cache/yum/arch/prod/repo/
packages/, but don’t install
yum install --downloadonly vsftpd
Download vsftpd package to cache

| **`--filter-???= Replace ??? with vendors, rpm-groups, arches, 
and others to filter output

| **`--changelog Display changelog information of package
