# Overview
Example of the approach to serve images for HDPI (retina) screens without html of backend changes.

### Base idea
First, setup cookie that indicates whether request came from HIDPI screen or not. It is done both with JavaScript and CSS hack (with additional request to server) to increase reliability.

Second, nginx checks - if `device-pixel-ratio` cookie is set and hidpi image variant is exists (notation - thumbnail must have `@<number>x` suffix, where `<number>` is scale multiplier - matches `device-pixel-ratio` cookie value).

Third, setup image sizes in html or css.

### How to run
To run project you could use Vagrant:

1. Install Vagrant [from official site] (https://www.vagrantup.com/downloads.html).
1. Install VirtualBox [from official site] (https://www.virtualbox.org/).
1. Open console and switch to folder with this project.
1. Run `vagrant up`.
1. Open browser and go to [virtual machine ip] (http://192.168.55.55).

To destroy virtual machine run `vagrant destroy` from project folder.  
More information about Vagrant can be found in it's [official documentation] (https://docs.vagrantup.com).

### Source
Based on the [Oliver Spindler article] (http://oliverspindler.com/articles/2012/04/05/conditionally-serving-high-resolution-images/).
