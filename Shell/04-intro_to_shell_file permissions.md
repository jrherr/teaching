### File Permissions & Users

chgrp
chmod

## File Permissions
chown = change the owner of a file
      ex --> chown bob hello.txt
chown user:bob report.txt = changes the user owning report.txt to 'user' and the group owning it to 'bob' -R = recursively affect all the sub folders
      ex --> chown -R bob:bob /home/Daniel
chmod = modify user access/permission – simple way
      u = user
      g = group
      o = other
      d = directory (if element is a directory)
      l = link (if element is a file link)
      r = read (read permissions)
      w = write (write permissions)
      x = eXecute (only useful for scripts and
      programs)

'+' means add a right
'-' means delete a right
'=' means affect a right
ex --> chmod g+w someFile.txt
      (add to current group the right to modify someFile.txt)
more info: man chmod


## Process Management

w = who is logged on and what they are doing
tload = graphic representation of system load average
      (quit with CTRL C)
ps = Static process list
      -ef --> ex: ps -ef | less
      -ejH --> show process hierarchy
      -u --> process's from current user
top = Dynamic process list
While in top:
• q to close top
• h to show the help
• k to kill a process
CTRL C to top a current terminal process
kill = kill a process
      You need the PID # of the process
             ps -u <AccountName> | grep <Application>
      Then
             kill <PID> .. .. ..
kill -9 <PID> = violent kill
killall = kill multiple process's
      ex --> killall locate
extras:
      sudo halt <-- to close computer
      sudo reboot <-- to reboot

## Create and modify user accounts

sudo adduser bob = root creates new user
sudo passwd <AccountName> = change a user's password
sudo deluser <AccountName> = delete an account
addgroup friends = create a new user group
delgroup friends = delete a user group
usermod -g friends <Account> = add user to a group usermod -g bob boby = change account name
usermod -aG friends bob = add groups to a user with- out loosing the ones he's already in

