#Sublime SFTP
How to set up Sublime with sftp to auto-sync files on your computer with Tufts CS homework servers.
Works for Mac

#Download sublime 3
- Download sublime from https://www.sublimetext.com/3

#Get Package Control for Sublime

- Open up your newly installed version of Sublime text
- Click View > Show Console

- Copy and pase the following python script
<pre><code>import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)</code></pre>

- Wait for the script to run
- Restart Sublime

For manual install instructions for package controll goto https://packagecontrol.io/installation

#Get SFTP Package
- Open up Sublime and hit command + shift + p
- In the window that appears, type 'Package Control: Install Package' and hit enter. The window will change to display a list of packages.
- Type SFTP and click on the first package that appears with the same name. Follow any prompts to
install the SFTP package.

If you have difficulties with this step, goto https://wbond.net/sublime_packages/sftp/installation

# Setting up SFTP with a folder of all your homework files
- Create a new local folder for all your homework.
- Open the folder in sublime. 
- Right click on the folder in the sidebar and select SFTP > Map to Remote… 
- Set the type, host, user, password, and remote path options as appropriate for Tufts CS. 

* host = homework.cs.tufts.edu
* user = [YOUR_UTLN]
* password = [YOUR PASSWORD]
* remote_path: "/h/[YOUR_UTLN]/[FOLDER_WITH_YOUR_WORK]"

For the remote path, it's important that you designate a path to a folder containing only
the subdirectories you want to sync. Otherwise you could be downloading a ton of files.

Then also configure the following options:

save_before_upload = true
upload_on_save = true 
sync_down_on_open = true
confirm_sync = false
extra_list_connections = 4
preserve_modification_times = true

For more info about this step goto https://wbond.net/sublime_packages/sftp/sidebar#SublimeSFTP

# Sync files and get to work!
Right click the folder you created
Select SFTP/FTP > Download Folder

Now you're ready to get working. Anytime you want to work remotely, just open the
folder you set up and edit files. Any changes are sync'd as soon as you save. 

When you SSH in to run your code on the homework servers, your files will
be up to date. Poof!

