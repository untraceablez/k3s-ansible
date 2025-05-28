load-balancer
=========

This role sets up the selected external load-balancer on the k3s cluster. 

Requirements
------------

No requirements aside from this running post-install for k3s.


Role Variables
--------------

* `load-balancer`: The load-balancer of your choice. This is either `metallb`, `cillium`, `traefik`, or `nginx`.  
* `floating-ip`: The external IP point for the cluster. Should be on your LAN.  
* `balancer-ip-range`: The subnet for load balancing. **This should not be your LAN network, and *must* be different!**


Dependencies
------------

This role has no dependencies.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - load-balancer

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
