+++
date = "2015-10-30"
draft = false
weight = 22
title = "Nova Commands"
+++


usage: `nova [optional arguments...] [subcommand]`  

**[optional arguments]** are shown at the bottom of this web page  



### Most popular nova commands

  - **nova list**  List instances, check status of instance
  - **nova image-list** List images
  - **nova flavor-list** List flavors
  - **nova boot --image IMAGE --flavor FLAVOR INSTANCE_NAME**  Boot an instance using flavor and image names (if names are unique)
  - **nova boot --image cirros-0.3.1-x86_64-uec --flavor m1.tiny MyUniqueInstanceName**  Boot an instance using an unique image name.
  - **nova show** ***NAME*** Get the details
  - **nova show INSTANCE-ID** Same as above but with ID instead of name
  - **nova console-log INSTANCE-ID** View the log 
  - **nova meta volumeTwoImage set newmeta='my meta data'**
  - **nova image-create volumeTwoImage snapshotOfVolumeImage**
  - **nova image-show snapshotOfVolumeImage**
  - **nova pause** ***NAME***
  - **nova unpause** ***NAME***
  - **nova suspend** ***NAME***
  - **nova resume** ***NAME***
  - **nova stop** ***NAME***
  - **nova start** ***NAME***
  - **nova delete** ***INSTANCE-ID***
  - **nova reboot** ***NAME***
  - **nova boot --user-data <FILE>** Injects file into booting instance's /var/lib/cloud directory
  - **nova secgroup-list**
  - **nova secgroup-add-group-rule default default icmp -1 -1** Add ping support (ICMP type and code, negative means unlimited)
  - **nova secgroup-add-group-rule default default tcp 22 22** Add SSH to security group


### Start all VMs on a given compute node

  `for inst in $(nova list --all-tenants --host r000001m001 --fields id,instance_name | grep "instance-" | cut -d ' ' -f 2); do nova start $inst; done`

  - This for loop loads variable $inst with instance ID
  - **nova list:** will list all vms which could be a really big list unless it is pared down.
  - The **--all-tenants** includes all tenants, not just the admin tenant
  - The **host r00001m001** is the compute node's ID that we want to evacuate, which you would have had to determine previously with a **nova host-list**
  - The **fields id** works with nova list and extracts values of specified fields. You can find valid field names in the Property column with: **nova show INSTANCE_ID** 
  - Then pipe this output to grep and filter on the string **instance-**
  - Then pipe this output to cut which will use a **d**elimiter = <space> and grab the second field
  - Now the variable $inst = the instance's ID
  - Start that instance with nova start $inst
  - End the for loop (bash for: do it again)


 
#### subcommand
  
`absolute-limits`             Print a list of absolute limits for a user.  
`add-fixed-ip`                Add new IP address on a network to server.  
`add-floating-ip`             DEPRECATED, use floating-ip-associate instead.  
`add-secgroup`                Add a Security Group to a server.  
`agent-create`                Create new agent build.  
`agent-delete`                Delete existing agent build.  
`agent-list`                  List all builds.  
`agent-modify`                Modify existing agent build.  
 
`aggregate-add-host`          Add the host to the specified aggregate.  
`aggregate-create`            Create a new aggregate with the specified details.  
`aggregate-delete`            Delete the aggregate.  
`aggregate-details`           Show details of the specified aggregate.  
`aggregate-list`              Print a list of all aggregates.  
`aggregate-remove-host`       Remove the specified host from the specified aggregate.  
`aggregate-set-metadata`      Update the metadata associated with the aggregate.  
`aggregate-update`            Update the aggregate's name and optionally availability zone.  
`availability-zone-list`      List all the availability zones.  
`backup`                      Backup a server by creating a 'backup' type snapshot.  
`boot`                        Boot a new server.  
`clear-password`              Clear the admin password for a server.  
`cloudpipe-configure`        Update the VPN IP/port of a cloudpipe instance.  
`cloudpipe-create`            Create a cloudpipe instance for the given project.  
`cloudpipe-list`              Print a list of all cloudpipe instances.  
`console-log`                 Get console log output of a server.  
`credentials`                 Show user credentials returned from auth.  
`delete`                      Immediately shut down and delete specified server(s).  
`diagnostics`                 Retrieve server diagnostics.  
 
`dns-create`                  Create a DNS entry for domain, name and IP.  
`dns-create-private-domain`   Create the specified DNS domain.  
`dns-create-public-domain`    Create the specified DNS domain.  
`dns-delete`                  Delete the specified DNS entry.  
`dns-delete-domain`           Delete the specified DNS domain.  
`dns-domains`                 Print a list of available dns domains.  
`dns-list`                    List current DNS entries for domain and IP or domain and name.  
`endpoints`                   Discover endpoints that get returned from the authenticate services.  
`evacuate`                    Evacuate server from failed host.  
`fixed-ip-get`                Retrieve info on a fixed IP.  
`fixed-ip-reserve`            Reserve a fixed IP.  
`fixed-ip-unreserve`          Unreserve a fixed IP.  

`flavor-access-add`           Add flavor access for the given tenant.  
`flavor-access-list`          Print access information about the given flavor.  
`flavor-access-remove`        Remove flavor access for the given tenant.  
`flavor-create`               Create a new flavor.  
`flavor-delete`               Delete a specific flavor.  
`flavor-key`                  Set or unset extra_spec for a flavor.  
`flavor-list`                 Print a list of available 'flavors' (sizes of servers).  
`flavor-show`                 Show details about the given flavor.  

`floating-ip-associate`  Associate a floating IP address to a server  
`floating-ip-bulk-create`     Bulk create floating IPs by range.  
`floating-ip-bulk-delete`     Bulk delete floating IPs by range.  
`floating-ip-bulk-list`       List all floating IPs.  
`floating-ip-create`          Allocate a floating IP for the current tenant.  
`floating-ip-delete`          De-allocate a floating IP.  
`floating-ip-disassociate`    Disassociate a floating IP address from a server.  
`floating-ip-list`            List floating IPs.  
`floating-ip-pool-list`       List all floating IP pools.  

`get-password`                Get the admin password for a server.  
`get-rdp-console`             Get a rdp console to a server.  
`get-serial-console`          Get a serial console to a server.  
`get-spice-console`           Get a spice console to a server.  
`get-vnc-console`             Get a vnc console to a server.  

`host-action`                 Perform a power action on a host.  
`host-describe`               Describe a specific host.  
`host-list`                   List all hosts by service.  
`host-update`                 Update host settings.  

`hypervisor-list`             List hypervisors.  
`hypervisor-servers`          List servers belonging to specific hypervisors.  
`hypervisor-show`             Display the details of the specified hypervisor.  
`hypervisor-stats`            Get hypervisor statistics over all compute nodes.  
`hypervisor-uptime`           Display the uptime of the specified hypervisor.  

`image-create`                Create a new image by taking a snapshot of a running server.  
`image-delete`                Delete specified image(s).  
`image-list`                  Print a list of available images to boot from.  
`image-meta`                  Set or Delete metadata on an image.  
`image-show`                  Show details about the given image.  

`interface-attach`            Attach a network interface to a server.  
`interface-detach`            Detach a network interface from a server.  
`interface-list`              List interfaces attached to a server.  

`keypair-add`                 Create a new key pair for use with servers.  
`keypair-delete`              Delete keypair given by its name.  
`keypair-list`                Print a list of keypairs for a user.  
`keypair-show`                Show details about the given keypair.  

`list`                        List active servers.  
`list-secgroup`               List Security Group(s) of a server.  
`live-migration`              Migrate running server to a new machine.  
`lock`                        Lock a server. A normal (non-admin) user will not be able to execute actions on a locked server.    
`meta`                        Set or Delete metadata on a server.  
`migrate`                     Migrate a server. The new host will be selected by the scheduler.  

`network-associate-host`      Associate host with network.  
`network-associate-project`   Associate project with network.  
`network-create`              Create a network.  
`network-delete`              Delete network by label or id.  
`network-disassociate`        Disassociate host and/or project from the given network.  
`network-list`                Print a list of available networks.  
`network-show`                Show details about the given network.  

`pause`                       Pause a server.  

`quota-class-show`            List the quotas for a quota class.  
`quota-class-update`          Update the quotas for a quota class.  
`quota-defaults`              List the default quotas for a tenant.  
`quota-delete`                Delete quota for a tenant/user so their quota will Revert back to default.  
`quota-show`                  List the quotas for a tenant/user.  
`quota-update`                Update the quotas for a tenant/user.  

`rate-limits`                 Print a list of rate limits for a user  
`reboot`                      Reboot a server.  
`rebuild`                     Shutdown, re-image, and re-boot a server.  
`refresh-network`             Refresh server network information.  
`remove-fixed-ip`            Remove an IP address from a server.  
`remove-floating-ip`          DEPRECATED, use floating-ip-disassociate instead.  
`remove-secgroup` Remove a Security Group from a server.  
`rename` Rename a server.  
`rescue` Reboots a server into rescue mode, which starts the machine from either the initial image or a specified image, attaching the current boot disk as secondary.  
`reset-network`   Reset network of a server.  
`reset-state`     Reset the state of a server.  
`resize`                      Resize a server.  
`resize-confirm`              Confirm a previous resize.  
`resize-revert`               Revert a previous resize (and return to the previous VM).  
`resume`                      Resume a server.  
`root-password`               Change the admin password for a server.  
`scrub`                       Delete networks and security groups associated with a project.  

`secgroup-add-default-rule`   Add a rule to the set of rules that will be added to the 'default' security group for new tenants.  
`secgroup-add-group-rule`     Add a source group rule to a security group.  
`secgroup-add-rule`           Add a rule to a security group.  
`secgroup-create`             Create a security group.  
`secgroup-delete`             Delete a security group.  
`secgroup-delete-default-rule` Delete a rule from the set of rules that will be added to the 'default' security group for new tenants.  
`secgroup-delete-group-rule`  Delete a source group rule from a security group.  
`secgroup-delete-rule`        Delete a rule from a security group.  
`secgroup-list`               List security groups for the current tenant.  
`secgroup-list-default-rules` List rules that will be added to the 'default' security group for new tenants.  
`secgroup-list-rules`         List rules for a security group.  
`secgroup-update`             Update a security group.  

`server-group-create`         Create a new server group with the specified details.  
`server-group-delete`         Delete specific server group(s).  
`server-group-get`            Get a specific server group.  
`server-group-list`           Print a list of all server groups.  

`service-delete`              Delete the service.  
`service-disable`             Disable the service.  
`service-enable`              Enable the service.  
`service-list`                Show a list of all running services. Filter by host & binary.  

`shelve`                      Shelve a server.  
`shelve-offload`              Remove a shelved server from the compute node.  
`show`                        Show details about the given server.  
`ssh`                         SSH into a server.  
`start`                       Start the server(s).  
`stop`                        Stop the server(s).  
`suspend`                     Suspend a server.  
`unlock`                      Unlock a server.  
`unpause`                     Unpause a server.  
`unrescue`                    Restart the server from normal boot disk again.  
`unshelve`                    Unshelve a server.  
`usage`                       Show usage data for a single tenant.  
`usage-list`                  List usage data for all tenants.  
`version-list`                List all API versions.  

`volume-attach`               Attach a volume to a server.  
`volume-create`               Add a new volume.  
`volume-delete`               Remove volume(s).  
`volume-detach`               Detach a volume from a server.  
`volume-list`                 List all the volumes.  
`volume-show`                Show details about a volume.  
`volume-snapshot-create`      Add a new snapshot.  
`volume-snapshot-delete`      Remove a snapshot.  
`volume-snapshot-list`        List all the snapshots.  
`volume-snapshot-show`        Show details about a snapshot.  
`volume-type-create`          Create a new volume type.  
`volume-type-delete`          Delete a specific volume type.  
`volume-type-list`            Print a list of available 'volume types'.  
`volume-update`               Update volume attachment.  

`x509-create-cert `           Create x509 cert for a user in tenant.  
`x509-get-root-cert`          Fetch the x509 root cert.  
`bash-completion`             Prints all of the commands and options to stdout so that the nova.bash_completion script doesn't have to hard code them.  
`help`                        Display help about this program or one of its subcommands.  
 
`baremetal-interface-add`     Add a network interface to a baremetal node.  
`baremetal-interface-list`    List network interfaces associated with a baremetal node.  
`baremetal-interface-remove`  Remove a network interface from a baremetal node.  
`baremetal-node-create`       Create a baremetal node.  
`baremetal-node-delete`       Remove a baremetal node and any associated interfaces.  
`baremetal-node-list`         Print list of available baremetal nodes.  
`baremetal-node-show`         Show information about a baremetal node.  

`cell-capacities`             Get cell capacities for all cells or a given cell.  
`cell-show`                   Show details of a given cell.  
`force-delete`                Force delete a server.  
`restore`                     Restore a soft-deleted server.  
`host-evacuate`               Evacuate all instances from failed host.  
`host-evacuate-live`          Live migrate all instances of the specified host to other available hosts.  
`host-servers-migrate`        Migrate all instances of the specified host to other available hosts.  
`instance-action`             Show an action.  
`instance-action-list`        List actions on a server.  
`list-extensions`             List all the os-api extensions that are available.  
`host-meta`                   Set or Delete metadata on all instances of a host.  
`migration-list`              Print a list of migrations.  
`net`                         DEPRECATED, Use tenant-network-show instead.  
`net-create`                  DEPRECATED, use tenant-network-create instead.  
`net-delete`                  DEPRECATED, use tenant-network-delete instead.  
`net-list`                    DEPRECATED, use tenant-network-list instead.  
`tenant-network-create`       Create a tenant network.  
`tenant-network-delete`       Delete a tenant network.  
`tenant-network-list`         List tenant networks.  
`tenant-network-show`         Show a tenant network.  

#### Optional arguments:  
`--version`                      show program's version number and exit  
`--debug`                        Print debugging output  
`--os-cache`                     Use the auth token cache. Defaults to False if env[OS_CACHE] is not set.  
`--timings`                      Print call timing info  
`--os-auth-token OS_AUTH_TOKEN`  Defaults to env[OS_AUTH_TOKEN]  
`--os-tenant-name <auth-tenant-name>`  Defaults to env[OS_TENANT_NAME].  
`--os-tenant-id <auth-tenant-id>` Defaults to env[OS_TENANT_ID].  
`--os-region-name <region-name>` Defaults to env[OS_REGION_NAME].  
`--os-auth-system <auth-system>` Defaults to env[OS_AUTH_SYSTEM].  
`--service-type <service-type>`  Defaults to compute for most actions  
`--service-name <service-name>`  Defaults to env[NOVA_SERVICE_NAME]  
`--volume-service-name <volume-service-name>` Defaults to env[NOVA_VOLUME_SERVICE_NAME]  
`--os-endpoint-type <endpoint-type>`  Defaults to env[NOVA_ENDPOINT_TYPE], env[OS_ENDPOINT_TYPE] or publicURL.  
`--os-compute-api-version <compute-api-ver>`  Accepts 1.1 or 3, defaults to env[OS_COMPUTE_API_VERSION].  
`--bypass-url <bypass-url>`      Use this API endpoint instead of the Service Catalog. Defaults to env[NOVACLIENT_BYPASS_URL]  
`--insecure`                     Explicitly allow client to perform "insecure" TLS (https) requests. The server's certificate will not be verified against any certificate authorities. This option should be used with caution.  
`--os-cacert <ca-certificate>`   Specify a CA bundle file to use in verifying a TLS (https) server certificate. Defaults to env[OS_CACERT].  
`--os-cert <certificate>`        Defaults to env[OS_CERT].  
`--os-key <key>`                 Defaults to env[OS_KEY].  
`--timeout <seconds>`            Set request timeout (in seconds).  
`--os-auth-url OS_AUTH_URL`      Authentication URL  
`--os-domain-id OS_DOMAIN_ID`    Domain ID to scope to  
`--os-domain-name OS_DOMAIN_NAME` Domain name to scope to  
`--os-project-id OS_PROJECT_ID`  Project ID to scope to  
`--os-project-name OS_PROJECT_NAME`  Project name to scope to  
`--os-project-domain-id OS_PROJECT_DOMAIN_ID` Domain ID containing project  
`--os-project-domain-name OS_PROJECT_DOMAIN_NAME` Domain name containing project  
`--os-trust-id OS_TRUST_ID`      Trust ID  
`--os-user-id OS_USER_ID`        User ID  
`--os-user-name OS_USERNAME, --os-username OS_USERNAME` Username  
`--os-user-domain-id OS_USER_DOMAIN_ID` User's domain id  
`--os-user-domain-name OS_USER_DOMAIN_NAME` User's domain name  
`--os-password OS_PASSWORD`      User's password  
  
