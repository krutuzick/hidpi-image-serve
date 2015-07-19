# hidpi-image-serve

### How to run
To run project you could use Vagrant:

1. Install vagrant [from official site] (https://www.vagrantup.com/downloads.html).
1. Install VirtualBox [from official site] (https://www.virtualbox.org/).
1. Open console and switch to folder with this project.
1. Run `vagrant up`
1. Open browser and go to [virtual machine ip] (http://192.168.55.55)

To destroy virtual machine run `vagrant destroy` from project folder.  
More information about Vagrant can be found in it's [official documentation] (https://docs.vagrantup.com)

Approach to serve images for HDPI (retina) screens without html of backend changes.  
Based on the [Oliver Spindler article] (http://oliverspindler.com/articles/2012/04/05/conditionally-serving-high-resolution-images/).
