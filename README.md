---
toc: true
---

{:toc max_level=3}

# Test

[DEMO](demo/demo)
[INSTALL](install)

# OpenStack Best Practices

# Cinder 

## Supported OpenStack Releases

* NexentaStor 4.x - Juno+

* NexentaStor 5.x - Juno+

* NexentaEdge 1.2 - Newton+

## Feature List

<table>
  <tr>
    <td>Feature</td>
    <td>NexentaStror 4</td>
    <td>NexentaStror 5.1</td>
    <td>NexentaEdge 2.1</td>
    <td>Required</td>
  </tr>
  <tr>
    <td>Create volume</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Delete volume</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Attach volume</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Detach volume</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Extend volume</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Create snapshot</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Delete snapshot</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Create volume from snapshot</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Create volume from image</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Clone volume</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Create image from volume</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Volume stats</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>implemented</td>
    <td>yes</td>
  </tr>
  <tr>
    <td>Migrate volume</td>
    <td>implemented</td>
    <td>implemented (NFS only)</td>
    <td>not implemented</td>
    <td>no</td>
  </tr>
  <tr>
    <td>Retype volume</td>
    <td>implemented</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>no</td>
  </tr>
  <tr>
    <td>Volume replication</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>no</td>
  </tr>
  <tr>
    <td>Consistency groups</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>no</td>
  </tr>
  <tr>
    <td>iSCSI LUN Mapping</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>no</td>
  </tr>
  <tr>
    <td>QoS (rate limit)</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>no</td>
  </tr>
  <tr>
    <td>Extend volume while attached</td>
    <td>implemented?</td>
    <td>implemented?</td>
    <td>implemented?</td>
    <td>no</td>
  </tr>
  <tr>
    <td>Snapshot Revert</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>not implemented</td>
    <td>no</td>
  </tr>
</table>


## Cinder Driver Prerequisites

#### NexentaStor 4.0

* Storage appliance must be configured and licensed

* Volume (zpool) must be created

* HA configured and VIP available

* (NFS only) NFS share created

* Storage Network configured between NS Appliance and OpenStack Hypervisors (Recommended 10GBE, MTU 9000)

#### NexentaStor 5.0

* Storage appliance must be configured and licensed

* Pool (zpool) must be created

* (iSCSI only) - Volume group must be created

* (NFS only) - File System must be created and shared over NFS

* Storage Network configured between NS Appliance and OpenStack Hypervisors (Recommended 10GBE, MTU 9000)

#### NexentaEdge 1.2

* System must be initialized and licensed

* Cluster/Tenant/Bucket creates

* NFS or iSCSI Gateway configured

* Storage Network configured between NexentaEdge Gateway and OpenStack Hypervisors (Recommended 10GBE, MTU 9000)

## Where to get Cinder Drivers?

It’s recommended to get the latest driver from Nexenta’s repository: [https://github.com/Nexenta/cinder/](https://github.com/Nexenta/cinder/)

The branches in the repository correspond with Openstack releases.

To following command can be used to download the exact version w/o having to switch branches

git clone -b stable/mitaka - this will download the exact version, no need to switch

Nexenta Drivers are located under the following path:
[https://github.com/Nexenta/cinder/tree/stable/mitaka/cinder/volume/drivers/nexenta](https://github.com/Nexenta/cinder/tree/stable/mitaka/cinder/volume/drivers/nexenta)

The path includes driver for NexentaStor 4.x, NexentaStor 5.x and NexnetaEdge 2.0. Make sure to copy the whole folder.

## Installation Steps

1. Determine cinder driver location path used in your environment

2. Clone or download the correct version of the drivers, unzip if downloaded and copy to the cinder location. For example drivers for Mitaka release:

<table>
  <tr>
    <td>git clone -b stable/mitaka https://github.com/Nexenta/cinder/
cp -rf cinder/cinder/volume/drivers/nexenta /usr/lib/python2.7/dist-packages/cinder/volume/drivers/</td>
  </tr>
</table>


3. Configure cinder.conf

4. Restart Cinder Service

    1. Need an example here

## NexentaStor 4.x NFS - List of all available options

<table>
  <tr>
    <td>Parameter name </td>
    <td>Default</td>
    <td>Choices</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>nexenta_dataset_compression</td>
    <td>on</td>
    <td>[on, off, gzip, gzip-1, gzip-2, gzip-3,  gzip-4, gzip-5, gzip-6, gzip-7, gzip-8,  gzip-9, lzjb, zle, lz4]</td>
    <td>Compression value for new ZFS folders.</td>
  </tr>
  <tr>
    <td>nexenta_dataset_description</td>
    <td></td>
    <td></td>
    <td>Human-readable description for the folder.</td>
  </tr>
  <tr>
    <td>nexenta_sparse</td>
    <td>False</td>
    <td>Boolean</td>
    <td>Enables or disables the creation of sparse datasets</td>
  </tr>
  <tr>
    <td>nexenta_rrmgr_compression</td>
    <td>0</td>
    <td>1..9</td>
    <td>Enable stream compression, level 1..9. 1 - gives best 
         speed; 9 - gives best compression.</td>
  </tr>
  <tr>
    <td>nexenta_rrmgr_tcp_buf_size</td>
    <td>4096</td>
    <td></td>
    <td>TCP Buffer size in KiloBytes.</td>
  </tr>
  <tr>
    <td>nexenta_rrmgr_connections</td>
    <td>2</td>
    <td></td>
    <td>Number of TCP connections.</td>
  </tr>
  <tr>
    <td>nexenta_shares_config</td>
    <td>/etc/cinder/nfs_shares</td>
    <td></td>
    <td>File with the list of available nfs shares (NexentaStor 4 only)</td>
  </tr>
  <tr>
    <td>nexenta_mount_point_base</td>
    <td>$state_path/mnt</td>
    <td></td>
    <td>Base directory that contains NFS share mount points</td>
  </tr>
  <tr>
    <td>nexenta_sparsed_volumes</td>
    <td>True</td>
    <td>Boolean</td>
    <td>Enables or disables the creation of volumes as 
         sparsed files that take no space. If disabled 
         (False), volume is created as a regular file, 
         which takes a long time.
</td>
  </tr>
  <tr>
    <td>nexenta_nms_cache_volroot</td>
    <td>True</td>
    <td>Boolean</td>
    <td>If set True cache NexentaStor appliance volroot option 
          value.</td>
  </tr>
</table>


#### NexentaStor 4.x NFS cinder.conf minimal config

<table>
  <tr>
    <td>     [ns_nfs]
volume_driver=cinder.volume.drivers.nexenta.nfs.NexentaNfsDriver
nexenta_shares_config=/home/ubuntu/shares.cfg
nfs_shares_config=/home/ubuntu/shares.cfg
volume_backend_name=ns_nfs
nas_secure_file_operations=False
</td>
  </tr>
</table>


**Note:** For NexentaStor 4.x NFS driver a shares config file must be present. This file should consist of 1 or multiple lines with 2 columns separated by a space. The first column represents the NFS filesystem path for the mount command, and the second is url for Rest calls.  Example:

<table>
  <tr>
    <td>10.0.0.1:/volumes/Vol1/nfs_share http://admin:nexenta@10.0.0.1:8457
10.0.0.100:/volumes/Vol2/cinder-volumes http://admin:secret@10.0.0.100:8457</td>
  </tr>
</table>


## NexentaStor 4.x iSCSI - List of all available options

<table>
  <tr>
    <td>Parameter name </td>
    <td>Default</td>
    <td>Choices</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>nexenta_host</td>
    <td></td>
    <td></td>
    <td>IP address of Nexenta SA</td>
  </tr>
  <tr>
    <td>nexenta_rest_port</td>
    <td>0</td>
    <td></td>
    <td>HTTP(S) port to connect to Nexenta REST API server. 
If it is equal zero, 8443 for HTTPS and 8080 for HTTP is used</td>
  </tr>
  <tr>
    <td>nexenta_rest_protocol</td>
    <td>auto</td>
    <td>[http, https, auto]</td>
    <td>Use http or https for REST connection</td>
  </tr>
  <tr>
    <td>nexenta_user</td>
    <td>admin</td>
    <td></td>
    <td>User name to connect to Nexenta SA,</td>
  </tr>
  <tr>
    <td>nexenta_password</td>
    <td>nexenta</td>
    <td></td>
    <td>Password to connect to Nexenta SA</td>
  </tr>
  <tr>
    <td>nexenta_dataset_compression</td>
    <td>on</td>
    <td>[on, off, gzip, gzip-1, gzip-2, gzip-3,  gzip-4, gzip-5, gzip-6, gzip-7, gzip-8,  gzip-9, lzjb, zle, lz4]
</td>
    <td>Compression value for new ZFS folders.</td>
  </tr>
  <tr>
    <td>nexenta_dataset_description</td>
    <td></td>
    <td></td>
    <td>Human-readable description for the folder.</td>
  </tr>
  <tr>
    <td>nexenta_blocksize</td>
    <td>4096</td>
    <td></td>
    <td>Block size for datasets (NStor4)</td>
  </tr>
  <tr>
    <td>nexenta_sparse</td>
    <td>False</td>
    <td>Boolean</td>
    <td>Enables or disables the creation of sparse datasets</td>
  </tr>
  <tr>
    <td>nexenta_rrmgr_compression</td>
    <td>0</td>
    <td>1..9</td>
    <td>Enable stream compression, level 1..9. 1 - gives best 
         speed; 9 - gives best compression.</td>
  </tr>
  <tr>
    <td>nexenta_rrmgr_tcp_buf_size</td>
    <td>4096</td>
    <td></td>
    <td>TCP Buffer size in KiloBytes.</td>
  </tr>
  <tr>
    <td>nexenta_rrmgr_connections</td>
    <td>2</td>
    <td></td>
    <td>Number of TCP connections.</td>
  </tr>
  <tr>
    <td>nexenta_iscsi_target_portal_port</td>
    <td>3260</td>
    <td></td>
    <td>Nexenta target portal port</td>
  </tr>
  <tr>
    <td>nexenta_volume</td>
    <td>cinder</td>
    <td></td>
    <td>SA Pool that holds all volumes</td>
  </tr>
  <tr>
    <td>nexenta_target_prefix</td>
    <td>iqn.1986-03.com.sun:02:cinder-</td>
    <td></td>
    <td>IQN prefix for iSCSI targets</td>
  </tr>
  <tr>
    <td>nexenta_target_group_prefix</td>
    <td>cinder</td>
    <td></td>
    <td>Prefix for iSCSI target groups on SA</td>
  </tr>
</table>


#### NexentaStor 4.x iSCSI cinder.conf minimal config

<table>
  <tr>
    <td>[ns_iscsi]
volume_driver=cinder.volume.drivers.nexenta.iscsi.NexentaISCSIDriver
volume_backend_name=ns_iscsi
nexenta_host=10.0.0.1
nexenta_rest_port=8457
nexenta_user=admin
nexenta_password=nexenta
nexenta_volume=Vol1
</td>
  </tr>
</table>


## NexentaStor 5.x NFS - List of all available options

<table>
  <tr>
    <td>Parameter name </td>
    <td>Default</td>
    <td>Choices</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>nexenta_rest_address</td>
    <td></td>
    <td></td>
    <td>IP address of NexentaEdge management REST API endpoint, can have multiple comma separated values</td>
  </tr>
  <tr>
    <td>nas_host</td>
    <td></td>
    <td></td>
    <td>Data IP address (VIP in case of HA)</td>
  </tr>
  <tr>
    <td>nexenta_rest_port</td>
    <td>0</td>
    <td></td>
    <td>HTTP(S) port to connect to Nexenta REST API server. 
If it is equal to zero, 8443 for HTTPS and 8080 for HTTP is used</td>
  </tr>
  <tr>
    <td>nexenta_use_https</td>
    <td>True</td>
    <td>Boolean</td>
    <td>Use secure HTTP for REST connection</td>
  </tr>
  <tr>
    <td>nexenta_user</td>
    <td>admin</td>
    <td></td>
    <td>User name to connect to Nexenta SA,</td>
  </tr>
  <tr>
    <td>nexenta_password</td>
    <td>nexenta</td>
    <td></td>
    <td>Password to connect to Nexenta SA</td>
  </tr>
  <tr>
    <td>nexenta_dataset_compression</td>
    <td>lz4</td>
    <td>[on, off, gzip, gzip-1, gzip-2, gzip-3,  gzip-4, gzip-5, gzip-6, gzip-7, gzip-8,  gzip-9, lzjb, zle, lz4]
</td>
    <td>Compression value for new ZFS datasets.</td>
  </tr>
  <tr>
    <td>nexenta_dataset_description</td>
    <td></td>
    <td></td>
    <td>Human-readable description for the folder.</td>
  </tr>
  <tr>
    <td>nexenta_mount_point_base</td>
    <td>$state_path/mnt</td>
    <td></td>
    <td>Base directory that contains NFS share mount points</td>
  </tr>
  <tr>
    <td>nexenta_sparsed_volumes</td>
    <td>True</td>
    <td>Boolean</td>
    <td>Enables or disables the creation of volumes as 
         sparsed files that take no space. If disabled 
         (False), volume is created as a regular file, 
         which takes a long time.
</td>
  </tr>
</table>


#### NexentaStor 5.x NFS cinder.conf minimal config

<table>
  <tr>
    <td>[ns5_nfs]
volume_driver=cinder.volume.drivers.nexenta.ns5.nfs.NexentaNfsDriver
nas_host=10.0.0.1 (for HA it must be VIP)
nexenta_rest_address=10.0.1.1 (for HA provide 2 IPs, comma separated)
nexenta_rest_port = 8443
nas_share_path=pool1/nfs_share
nexenta_user = admin
nexenta_password = Nexenta@1
nas_mount_options = vers=4
volume_backend_name = ns5_nfs
nexenta_sparsed_volumes = True
nas_secure_file_operations = False</td>
  </tr>
</table>


## NexentaStor 5.x iSCSI - List of all available options

<table>
  <tr>
    <td>Parameter name </td>
    <td>Default</td>
    <td>Choices</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>nexenta_rest_address</td>
    <td></td>
    <td></td>
    <td>IP address of NexentaStor management REST API endpoint, can have multiple comma separated values</td>
  </tr>
  <tr>
    <td>nexenta_host</td>
    <td></td>
    <td></td>
    <td>IP address of Nexenta SA</td>
  </tr>
  <tr>
    <td>nexenta_rest_port</td>
    <td>0</td>
    <td></td>
    <td>HTTP(S) port to connect to Nexenta REST API server. 
If it is equal zero, 8443 for HTTPS and 8080 for HTTP is used</td>
  </tr>
  <tr>
    <td>nexenta_use_https</td>
    <td>True</td>
    <td>Boolean</td>
    <td>Use secure HTTP for REST connection</td>
  </tr>
  <tr>
    <td>nexenta_user</td>
    <td>admin</td>
    <td></td>
    <td>User name to connect to Nexenta SA,</td>
  </tr>
  <tr>
    <td>nexenta_password</td>
    <td>nexenta</td>
    <td></td>
    <td>Password to connect to Nexenta SA</td>
  </tr>
  <tr>
    <td>nexenta_dataset_compression</td>
    <td>lz4</td>
    <td>[on, off, gzip, gzip-1, gzip-2, gzip-3,  gzip-4, gzip-5, gzip-6, gzip-7, gzip-8,  gzip-9, lzjb, zle, lz4]
</td>
    <td>Compression value for new ZFS datasets.</td>
  </tr>
  <tr>
    <td>nexenta_dataset_description</td>
    <td></td>
    <td></td>
    <td>Human-readable description for the folder.</td>
  </tr>
  <tr>
    <td>nexenta_ns5_blocksize</td>
    <td>32 (kilobytes)</td>
    <td></td>
    <td>Block size for datasets (Nstor5)</td>
  </tr>
  <tr>
    <td>nexenta_sparse</td>
    <td>False</td>
    <td>Boolean</td>
    <td>Enables or disables the creation of sparse datasets</td>
  </tr>
  <tr>
    <td>nexenta_iscsi_target_portal_port</td>
    <td>3260</td>
    <td></td>
    <td>Nexenta target portal port</td>
  </tr>
  <tr>
    <td>nexenta_volume</td>
    <td>cinder</td>
    <td></td>
    <td>SA Pool that holds all volumes</td>
  </tr>
  <tr>
    <td>nexenta_target_prefix</td>
    <td>iqn.1986-03.com.sun:02:cinder-</td>
    <td></td>
    <td>IQN prefix for iSCSI targets</td>
  </tr>
  <tr>
    <td>nexenta_target_group_prefix</td>
    <td>cinder</td>
    <td></td>
    <td>Prefix for iSCSI target groups on SA</td>
  </tr>
  <tr>
    <td>nexenta_volume_group</td>
    <td>iscsi</td>
    <td></td>
    <td>Volume group for NStor5</td>
  </tr>
  <tr>
    <td>nexenta_iscsi_target_portals</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>


#### NexentaStor 5.x iSCSI cinder.conf minimal config

<table>
  <tr>
    <td>[ns5_iscsi]
volume_driver = cinder.volume.drivers.nexenta.ns5.iscsi.NexentaISCSIDriver
volume_backend_name = ns5_iscsi
nexenta_host = 10.0.0.1 (for HA it must be VIP)
nexenta_rest_address=10.0.1.1 (for HA provide 2 IPs, comma separated)
nexenta_rest_port = 8443
nexenta_user = admin
nexenta_password = Nexenta@1
nexenta_volume = pool1
nexenta_volume_group = iscsi</td>
  </tr>
</table>


## NexentaEdge 1.2 iSCSI - List of all available options

<table>
  <tr>
    <td>Parameter name </td>
    <td>Default</td>
    <td>Choices</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>nexenta_rest_address</td>
    <td></td>
    <td></td>
    <td>IP address of NexentaEdge management REST API endpoint</td>
  </tr>
  <tr>
    <td>nexenta_rest_port</td>
    <td>0</td>
    <td></td>
    <td>HTTP(S) port to connect to Nexenta REST API server. 
If it is equal zero, 8443 for HTTPS and 8080 for HTTP is used</td>
  </tr>
  <tr>
    <td>nexenta_rest_protocol</td>
    <td>auto</td>
    <td>[http, https, auto]</td>
    <td>Use http or https for REST connection</td>
  </tr>
  <tr>
    <td>nexenta_blocksize</td>
    <td>4096</td>
    <td></td>
    <td>Block size for datasets (NStor4)</td>
  </tr>
  <tr>
    <td>nexenta_nbd_symlinks_dir</td>
    <td>/dev/disk/by-path</td>
    <td></td>
    <td>NexentaEdge logical path of directory to store symbolic  \links to NBDs.</td>
  </tr>
  <tr>
    <td>nexenta_rest_user</td>
    <td>admin</td>
    <td></td>
    <td>User name to connect to NexentaEdge</td>
  </tr>
  <tr>
    <td>nexenta_rest_password</td>
    <td>nexenta</td>
    <td></td>
    <td>Password to connect to NexentaEdge</td>
  </tr>
  <tr>
    <td>nexenta_lun_container</td>
    <td></td>
    <td></td>
    <td>NexentaEdge logical path of bucket for LUNs</td>
  </tr>
  <tr>
    <td>nexenta_iscsi_service</td>
    <td></td>
    <td></td>
    <td>NexentaEdge iSCSI service name</td>
  </tr>
  <tr>
    <td>nexenta_client_address</td>
    <td></td>
    <td></td>
    <td>NexentaEdge iSCSI Gateway client address for non-VIP service</td>
  </tr>
  <tr>
    <td>nexenta_chunksize</td>
    <td>32768</td>
    <td></td>
    <td>NexentaEdge iSCSI LUN object chunk size</td>
  </tr>
</table>


#### NexentaEdge 1.2 iSCSI cinder.conf minimal config

<table>
  <tr>
    <td>[nedge_iscsi]
volume_driver=cinder.volume.drivers.nexenta.nexentaedge.iscsi.NexentaEdgeISCSIDriver
volume_backend_name = nedge
nexenta_rest_address = 10.0.0.1
nexenta_rest_port = 8080
nexenta_rest_protocol = http
nexenta_iscsi_target_portal_port = 3260
nexenta_rest_user = admin
nexenta_rest_password = nexenta
nexenta_lun_container = cl/tn/bk
nexenta_iscsi_service = iscsi
nexenta_client_address = 10.0.1.1</td>
  </tr>
</table>


After configuring the cinder.conf, restart the cinder-volume service

service cinder-volume restart (may differ depending on OS)

## NexentaStor 4.x vs. 5.x Options Conversion Table

<table>
  <tr>
    <td>4.x param</td>
    <td>5.x param</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>uses same param for rest and data 
(nexenta_host)</td>
    <td>nexenta_rest_address</td>
    <td>4.x does not have separate value for Rest API management</td>
  </tr>
  <tr>
    <td>nexenta_rest_protocol</td>
    <td>nexenta_use_https</td>
    <td></td>
  </tr>
  <tr>
    <td>nexenta_folder</td>
    <td>volume_group</td>
    <td>iSCSI only for 5.x, both protocols for 4.x</td>
  </tr>
  <tr>
    <td>nfs_shares_config</td>
    <td>nas_share_path</td>
    <td>5.x does not use shares.cfg</td>
  </tr>
  <tr>
    <td>nexenta_iscsi_target_portal_groups</td>
    <td>nexenta_iscsi_target_portals
and
nexenta_iscsi_target_portal_port</td>
    <td>4.x exposes TPGs while 5.x creates them using list of portals (IPs)</td>
  </tr>
</table>


## iSCSI Multipath

Openstack Nova provides the ability to use iSCSI Multipath. To enable Multipath you need to add following line into nova.conf in the [libvirt] section:

[libvirt]

iscsi_use_multipath = True

For this change to take place you need to restart nova-compute service:
service restart nova-compute

## Backup

This section describes how to configure the cinder-backup service and cinder NFS driver on top NexentaStor NFS share. Official documentation link: [NFS backup driver](https://docs.openstack.org/newton/config-reference/block-storage/backup/nfs-backup-driver.html)

Example section for cinder.conf:

<table>
  <tr>
    <td>[DEFAULT]
backup_driver = cinder.backup.drivers.nfs
backup_share = 10.1.1.1:/pool/nfs/backup
backup_mount_options = vers=4</td>
  </tr>
</table>


Note: 10.1.1.1 - IP address of NexentaStor, /pool/nfs/backup - NFS share path.

Steps for NexentaStor 4.x:

<table>
  <tr>
    <td>nmc@host1:/$ create folder pool/nfs/backup
nmc@host1:/$ share folder pool/nfs/backup nfs                                                                                           
Auth Type            : sys
Anonymous            : false
Read-Write           :
Read-Only            : 
Root                 : 
Extra Options        : uidmap=*:root:@10.1.1.2
Recursive            : true
Modifed NFS share for folder 'pool/nfs/backup'</td>
  </tr>
</table>


Note: 10.1.1.2 - IP address of Openstack Cinder host.

Steps for NexentaStor 5.x:

<table>
  <tr>
    <td>CLI@host> filesystem create -p pool/nfs/backup
CLI@host> nfs share -o uidMap='*:root:@10.1.1.2' pool/nfs/backup</td>
  </tr>
</table>


Note: 10.1.1.2 - IP address of Openstack Cinder host.

## Cinder and Replication

* Replication on Consistency group level

* Replication of clones will result in a full filesystems (Not efficient from capacity perspective)

* Cinder snapshots are omitted in replication in 5.1.x (We expect fix in 5.2FP1)

## Troubleshooting

grep for "Traceback" in your Openstack logs folder, default is

/var/log/<openstack-project>/, for example:
/var/log/cinder/cinder-voume.log

Most of the errors related to storage are in Cinder or Nova logs.

If the error is not self explanatory, enable the debug logging, restart the service and try to reproduce the error. Debug loggings will trace all calls to Nexenta, which allows to narrow down the possible cause of the error.

To enable debug in cinder, add the following line to cinder.conf:
debug=True

And restart cinder-volume:
service cinder-volume restart

## Known Issues

* Replication of clones

* Cinder Creation after failover fails

    * [https://jira.nexenta.com/browse/NEX-15375](https://jira.nexenta.com/browse/NEX-15375)

* Cinder volume mount after failover goes into read only

    * [https://jira.nexenta.com/browse/NEX-15375](https://jira.nexenta.com/browse/NEX-15375)

Do we need to talk about SSL issues?
	driver_ssl_cert_verify = false 

Only depends on the certificate that is used.

# Glance

What it is:

How to set it up:

Prerequisites

Steps

Validation

# Manila

### Overview

#### ![image alt text](image_0.png)

#### **Supported operations are:**

* Create NFS share.

* Delete NFS share.

* Extend NFS share

* Allow NFS share access.

* Only IP access type is supported for NFS.

* RW and RO access is supported.

* Deny NFS share access

* Create snapshot

* Delete snapshot

* Create share from snapshot

* Thin/thick provisioning

### Requirements

* NexentaStor Appliance pre-provisioned and licensed, etc

* OpenStack Preprovisioned with Manila Plugin

How to setup Manila Plugin

### Deployment

Devstack environment:

<table>
  <tr>
    <td>root# useradd -s /bin/bash -d /opt/stack -m stack
root# echo "stack ALL=(ALL) NOPASSWD: ALL" | tee /etc/sudoers.d/stack
root# passwd stack</td>
  </tr>
</table>


<table>
  <tr>
    <td>stack$ git clone https://git.openstack.org/openstack-dev/devstack
stack$ cd devstack
stack$ cat local.conf <<'EOF'
[[local|localrc]]
ADMIN_PASSWORD=secret
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD
USE_SCREEN=True
RECLONE=True
enable_plugin manila https://github.com/openstack/manila
EOF

stack$ ./stack.sh</td>
  </tr>
</table>


manila.conf driver section examples:

NStor4:

<table>
  <tr>
    <td>enabled_share_backends = ns4_nfs
enabled_share_protocols = NFS
[ns4_nfs]
service_instance_user = manila
service_image_name = manila-service-image
path_to_private_key = /home/ubuntu/.ssh/id_rsa
path_to_public_key = /home/ubuntu/.ssh/id_rsa.pub
share_backend_name = <backend name to be used in share_types>
driver_handles_share_servers = False
share_driver = manila.share.drivers.nexenta.nexenta_nas.NexentaNasDriver
nexenta_host = <Nexenta appliance IP>
nexenta_volume = <volume name on appliance>
nexenta_nfs_share = <nfs_share_name>
nexenta_user = <NexentaStor username>
nexenta_password = <NexentaStor password>
nexenta_thin_provisioning = False/True</td>
  </tr>
</table>


NStor5:

<table>
  <tr>
    <td>enabled_share_backends = ns5_nfs
enabled_share_protocols = NFS
[ns5_nfs]
service_instance_user = manila
service_image_name = manila-service-image
path_to_private_key = /home/ubuntu/.ssh/id_rsa
path_to_public_key = /home/ubuntu/.ssh/id_rsa.pub
share_backend_name = <backend name to be used in share_types>
driver_handles_share_servers = False
share_driver = manila.share.drivers.nexenta.nexenta_nas.NexentaNasDriver
nexenta_host = <Nexenta appliance IP>
nexenta_rest_port = 8443
nexenta_volume = <pool name on appliance>
nexenta_share = <dataset name within the pool>
nexenta_user = <NexentaStor username>
nexenta_password = <NexentaStor password>
nexenta_thin_provisioning = False/True</td>
  </tr>
</table>


List of all available options:

<table>
  <tr>
    <td>Parameter name</td>
    <td>Default</td>
    <td>Choices</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>nexenta_host</td>
    <td></td>
    <td></td>
    <td>IP address of Nexenta storage appliance.</td>
  </tr>
  <tr>
    <td>nexenta_rest_port</td>
    <td>8457</td>
    <td></td>
    <td>Port to connect to Nexenta REST API server.</td>
  </tr>
  <tr>
    <td>nexenta_retry_count</td>
    <td>6</td>
    <td></td>
    <td>Number of retries for unsuccessful API calls.</td>
  </tr>
  <tr>
    <td>nexenta_rest_protocol</td>
    <td>auto</td>
    <td>[http, https, auto]</td>
    <td>Use http or https for REST connection .</td>
  </tr>
  <tr>
    <td>nexenta_user</td>
    <td>admin</td>
    <td></td>
    <td>User name to connect to Nexenta SA.</td>
  </tr>
  <tr>
    <td>nexenta_password</td>
    <td></td>
    <td></td>
    <td>Password to connect to Nexenta SA.</td>
  </tr>
  <tr>
    <td>nexenta_volume</td>
    <td>volume1</td>
    <td></td>
    <td>Volume name on NexentaStor4</td>
  </tr>
  <tr>
    <td>nexenta_pool</td>
    <td>pool1</td>
    <td></td>
    <td>Pool name on NexentaStor5.</td>
  </tr>
  <tr>
    <td>nexenta_mount_point_base</td>
    <td>$state_path/mnt</td>
    <td></td>
    <td>Base directory that contains NFS share mount points.</td>
  </tr>
  <tr>
    <td>nexenta_nfs_share</td>
    <td>nfs_share</td>
    <td></td>
    <td>Parent folder on NexentaStor that will contain all manila folders.</td>
  </tr>
  <tr>
    <td>nexenta_dataset_compression</td>
    <td>on</td>
    <td>[on, off, gzip, gzip-1, gzip-2, gzip-3,  gzip-4, gzip-5, gzip-6, gzip-7, gzip-8,gzip-9, lzjb, zle, lz4]
</td>
    <td>Compression value for new ZFS folders.</td>
  </tr>
  <tr>
    <td>nexenta_dataset_dedupe</td>
    <td>off</td>
    <td>[on, off, sha256, verify]</td>
    <td>Deduplication value for new ZFS folders.</td>
  </tr>
  <tr>
    <td>nexenta_thin_provisioning</td>
    <td>True</td>
    <td>Boolean</td>
    <td>If True shares will not be space guaranteed and overprovisioning will be enabled.'
</td>
  </tr>
</table>


Docs - https://confluence.nexenta.com/display/CO/Project%3A+OpenStack+Manila

[https://confluence.nexenta.com/display/SUP/OpenStack+-+Support#expand-InstallingUpgradingNexentaManilaDriver](https://confluence.nexenta.com/display/SUP/OpenStack+-+Support#expand-InstallingUpgradingNexentaManilaDriver)

[https://confluence.nexenta.com/display/CO/Manila+User+Guide#expand-NexentaStor4xdriverconfiguration](https://confluence.nexenta.com/display/CO/Manila+User+Guide#expand-NexentaStor4xdriverconfiguration)


