
### install Salt Latest version

curl -L https://bootstrap.saltstack.com -o install_salt.sh

## install salt with Master and Minion

sudo sh install_salt.sh -P -M

## installation complete!

sudo vi /etc/salt/minion

### update the minion id and master 


master: localhost
id: admaticweb1

root@ip-172-31-84-23:/home/hadoop# sudo service salt-master restart                                                                                         [24/24]
salt-master stop/waiting
salt-master start/running, process 18439
root@ip-172-31-84-23:/home/hadoop# sudo service salt-minion restart
salt-minion stop/waiting
salt-minion start/running, process 18898
root@ip-172-31-84-23:/home/hadoop# sudo tail -100 /var/log/salt/minion


root@ip-172-31-84-23:/home/hadoop# sudo tail -100 /var/log/salt/master

root@ip-172-31-84-23:/home/hadoop#
root@ip-172-31-84-23:/home/hadoop# netstat -nltp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1023/sshd
tcp        0      0 0.0.0.0:4505            0.0.0.0:*               LISTEN      18448/python
tcp        0      0 0.0.0.0:4506            0.0.0.0:*               LISTEN      18454/python
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1174/mysqld
tcp6       0      0 :::22                   :::*                    LISTEN      1023/sshd
tcp6       0      0 :::443                  :::*                    LISTEN      1685/docker-proxy
root@ip-172-31-84-23:/home/hadoop#
root@ip-172-31-84-23:/home/hadoop# sudo salt-key
Accepted Keys:
Denied Keys:
Unaccepted Keys:
admaticweb1
Rejected Keys:
root@ip-172-31-84-23:/home/hadoop# sudo salt-key -a admaticweb1
The following keys are going to be accepted:
Unaccepted Keys:
admaticweb1
Proceed? [n/Y] Y
Key for minion admaticweb1 accepted.
root@ip-172-31-84-23:/home/hadoop# sudo salt-key
Accepted Keys:
admaticweb1
Denied Keys:
Unaccepted Keys:
Rejected Keys:
root@ip-172-31-84-23:/home/hadoop# sudo salt '*' test.ping
admaticweb1:
    True
root@ip-172-31-84-23:/home/hadoop#

hadoop@ip-172-31-82-145:~$ sudo salt '*' sys.list_functions test
godisgreat:
    - test.arg
    - test.arg_clean
    - test.arg_repr
    - test.arg_type
    - test.assertion
    - test.attr_call
    - test.collatz
    - test.conf_test
    - test.cross_test
    - test.echo
    - test.exception
    - test.false
    - test.fib
    - test.get_opts
    - test.kwarg
    - test.module_report
    - test.not_loaded
    - test.opts_pkg
    - test.outputter
    - test.ping
    - test.provider
    - test.providers
    - test.rand_sleep
    - test.rand_str
    - test.random_hash
    - test.retcode
    - test.sleep
    - test.stack
    - test.true
    - test.try
    - test.tty
    - test.version
    - test.versions
    - test.versions_information
    - test.versions_report
hadoop@ip-172-31-82-145:~$ sudo salt --version
salt 2018.3.0 (Oxygen)
hadoop@ip-172-31-82-145:~$
