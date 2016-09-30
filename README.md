MTN.*NIX.11 LDAP
---

***Student***: [Uladzislau Charches](https://upsa.epam.com/workload/employeeView.do?employeeId=4060741400038705754#emplTab=general)

# LDAP
To use LDAP we need to install ldap and configured it.

# yum install openldap-servers openldap-clients

**Configure DB**

# cp /usr/share/openldap-servers/DB_CONFIG.example /var/lib/ldap/DB_CONFIG

#Verify ownerships on db location

chown -R ldap:ldap /var/lib/ldap

# generate root password
slappasswd

# create configuration
/etc/openldap/slapd.conf 

# Check the config file
slaptest

# Start slapd daemon
service slapd start

**Usefull commands:**

Add  data to base : ldapadd -x -D "cn=admin,dc=mnt,dc=lab" -W -f /etc/openldap/ldap-init.ldif

ldapadd -x -D "cn=admin,dc=mnt,dc=lab" -W -f /etc/openldap/username.ldif

Check data from base : ldapsearch -h localhost -D "cn=admin,dc=mnt,dc=lab" -W -b "dc=mnt,dc=lab" -s sub "objectclass=*"

ldapsearch -h localhost -D "cn=admin,dc=mnt,dc=lab" -W -b "dc=mnt,dc=lab" -s sub "uid=userinldap"

2. Installing phpldapadmin

#yum install -y http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm

#yum install -y phpldapadmin

Edit vhost
  
Comments 2 lines in /etc/phpldapadmin/config.php:

$servers->setValue('login','attr','dn');

//$servers->setValue('login','attr','uid');

After service httpd start and everything OK



**Screenshots**

![1](screens/1.png)
![2](screens/2.png)
![3](screens/3.png)
![4](screens/4.png)
![5](screens/5.png)
![6](screens/6.png)
