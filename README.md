this is munin-plugin for Java GC stats, modified to run on lichess instances.

plugin call jps and jstat. - http://docs.oracle.com/javase/7/docs/technotes/tools/share/jstat.html

tested on JDK1.8 and recent (2014+) Ubuntus.


# 1.Install

    $ cd /usr/share/munin/plugins/
    $ sudo wget https://raw.github.com/kistvan/munin-jstat/master/jstat-gcutil -O jstat-gcutil
    $ sudo wget https://raw.github.com/kistvan/munin-jstat/master/jstat-gcutil-gccount -O jstat-gcutil-gccount
    $ sudo wget https://raw.github.com/kistvan/munin-jstat/master/jstat-gcutil-gctime -O jstat-gcutil-gctime
    $ sudo wget https://raw.github.com/kistvan/munin-jstat/master/jstat-gcutil-gccapacity -O jstat-gcutil-gccapacity
    $ sudo chmod a+x jstat-gcutil*
    $ sudo ln -s /usr/share/munin/plugins/jstat-gcutil /etc/munin/plugins/jstat-gcutil
    $ sudo ln -s /usr/share/munin/plugins/jstat-gcutil-gccount /etc/munin/plugins/jstat-gcutil-gccount
    $ sudo ln -s /usr/share/munin/plugins/jstat-gcutil-gctime /etc/munin/plugins/jstat-gcutil-gctime
    $ sudo ln -s /usr/share/munin/plugins/jstat-gcutil-gccapacity /etc/munin/plugins/jstat-gcutil-gccapacity
    $ sudo -e /etc/munin/plugin-conf.d/munin-node

edit munin-node config file.

    [jstat-gcutil*]
    user root # root or java application PID accessible user
    env.JAVA_HOME /usr/java/latest #default /usr/java/latest

test and run.

    $ sudo munin-run jstat-gcutil
    $ sudo munin-run jstat-gcutil-gccount
    $ sudo munin-run jstat-gcutil-gctime
    $ sudo munin-run jstat-gcutil-gccapacity
    $ sudo service munin-node reload

