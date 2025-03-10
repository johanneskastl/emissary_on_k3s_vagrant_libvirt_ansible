# emissary_on_k3s_vagrant_libvirt_ansible

Vagrant-libvirt setup that creates a VM with k3s and
[Emissary](https://github.com/emissary-ingress/emissary) as the ingress
controller.

Default OS is openSUSE Leap 15.5, but that can be changed in the Vagrantfile.
Please be aware, that this might break the Ansible provisioning.

## Vagrant

1. You need `vagrant`, obviously. And `git`. And Ansible...
1. Fetch the box, per default this is `opensuse/Leap-15.5.x86_64`, using
   `vagrant box add opensuse/Leap-15.5.x86_64`.
1. Make sure the git submodules are fully working by issuing
   `git submodule init && git submodule update`
1. Run `vagrant up`
1. Run `kubectl --kubeconfig ansible/k3s-kubeconfig get nodes` and you should
   see your server.
1. Open the URL that was printed out at the end of the Ansible provisioning, and
   you should see the Nginx page.
   The URL should look something like this:
   `http://nginx.192.0.2.13.sslip.io`
1. Party!

## Cleaning up

The VMs can be torn down after playing around using `vagrant destroy`. This will
also remove the kubeconfig file `ansible/k3s-kubeconfig`.
