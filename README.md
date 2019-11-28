# Raspberry-Pi-4-Net-ISP-Balance
This repositiory is for tracking the changes to a script for creating a load balanced setup between multiple ISPs
This just lists out the commands that you will need to execute on the Raspberry pi to get it setup.

You'll need to read the document here:
http://lstein.github.io/Net-ISP-Balance/

Before Heading 2 use this code instead of what they have listed on the document's site:
***note:*** all perl steps are done with sudo since pearl installs modules local to the use that executed it (yes there is probably a better/safer way)
<code>
#Basic Raspbery pi updates
sudo apt update
sudo apt upgrade

#install git to pull the repo
sudo apt install git

#pull the repo and change to that directory
git clone https://github.com/lstein/Net-ISP-Balance.git
cd Net-ISP-Balance

#This app assists with Module installs
sudo cpan App::cpanminus
sudo cpanm Module::Build

#Next command takes a while (which is a dependency of Net-ISP-Balance, which would get installed at "installdeps")
#This just speeds up the steps ahead
sudo cpan Net::Netmask

#install Net-ISP-Balance (close to step 2 on the web doc listed above)
sudo perl ./Build.PL
sudo ./Build installdeps
sudo ./Build test
sudo ./Build install
</code>

from there continue with the install at http://lstein.github.io/Net-ISP-Balance/

