#GlusterFS 3.4.0 Release Notes 

## Major Changes and Features

### Dual Licensing

All of GlusterFS 3.4.0 is available under this dual License:

- GNU Lesser General Public License, version 3 or any later version (LGPLv3 or later), 

    or 

- GNU General Public License, version 2 (GPLv2)


### libgfapi


libgfapi provides API access to data that is stored in gluster volumes. Description of the API can be found [here] (https://forge.gluster.org/glusterfs-core/glusterfs/blobs/release-3.4/api/src/glfs.h).

qemu and samba are already integrated with libgfapi. You can now access gluster volumes directly from qemu and samba without having to come through a regular filesystem mount point.

### Quorum enforcement from Trusted Storage Pool

Quorum can now be enforced from the Trusted Storage Pool. Connectivity information present in glusterd is used to determine quorum. Server Side quorum can be enabled by:

*\#gluster volume set <volname\> cluster.server-quorum-type server*

*\#gluster volume set <volname\> cluster.server-quorum-ratio <percentage\>*

More details about this feature can be found [here] (http://www.gluster.org/community/documentation/index.php/Features/Server-quorum).


### Improvements for Virtual Machine Image Storage

A number of improvements have been performed to let Gluster volumes provide storage for Virtual Machine Images. Some of them include:

- qemu - libgfapi integration.
- Causal ordering in write-behind translator.
- Tunables for a gluster volume in group-virt.example.

The above result in significant improvements in performance for VM hosting. 


### Synchronous Replication Improvements

GlusterFS 3.4 features significant improvements in performance for the replication (AFR) translator. This is in addition to bug fixes for volumes that used replica 3. 


### Open Cluster Framework compliant Resource Agents

Resource Agents (RA) plug glusterd into Open Cluster Framework
(OCF) compliant cluster resource managers, like Pacemaker.
    
The glusterd RA manages the glusterd daemon like any upstart or systemd job would, except that Pacemaker can do it in a cluster-aware fashion.
    
The volume RA starts a volume and monitors individual brick's daemons in a cluster aware fashion, recovering bricks when their processes fail.


### POSIX ACL support over NFSv3

setfacl and getfacl commands now can be used on a nfs mount that exports a gluster volume to set or read posix ACLs.

### 3.3.x compatibility

The new op-version infrastructure provides compatibility with 3.3.x release of GlusterFS. 3.3.x clients can talk to 3.4.x servers and the vice-versa is also possible. 

If a volume option that corresponds to 3.4 is enabled, then 3.3 clients cannot mount the volume.

### Packaging changes

New RPMs for libgfapi and OCF RA are present with 3.4.0.

### Experimental Features

RDMA-connection manager (RDMA-CM), Block Device translator and support for NUFA available as experimental features with this release.


## Minor Improvements:

- The Ext4 file system change which affected readdir workloads for Gluster volumes has been addressed.

- More options for selecting read-child with afr available now.

- Custom layouts possible with distribute translator.

- No 32-aux-gid limit

- SSL support for socket connections.

- Known issues with replica count greater than 2 addressed.

- quick-read and md-cache translators have been refactored.

- open-behind translator introduced.

- Ability to avoid glusterfs bind to reserved ports.

- statedumps are now created in /var/run/gluster instead of /tmp by default.

### Known Issues:













