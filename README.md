{:toc}
# Test

[DEMO 1](demo/demo)
[DEMO 2](demo)

# OpenStack Best Practices


## Cinder Feature List
| Feature | NexentaStor 4.x | NexentaStor 5.x |
|---|----|----|
| Create Volume | Implemented | Implemented |


### Requirements and Limitations
It is highly recommended that you run NexentaEdge DevOps Edition on a system with at least 16GB RAM.

| Requirement | Notes |
|---------------|---------|
| OS|Ubuntu 16.04 LTS, CentOS/RHEL 7.2 (with ELRepo enabled) |
| Kernel Version | 4.4 or higher |
| Docker Version | 1.12 or higher |
| CPU | 4 cores minimally recommended |
| Memory | 16GB Minimum + 2GB x # of HDDs |
| Management Network | Connected to management 1G switch (optional) |
| Client I/O Network | Shared with clients network, 1G - 100G |
| Replicast I/O Network | Dedicated, VLAN isolated networking, MTU 9000 (required), 1G - 100G |
| Minimum individual Disk size | 1GB |
| Minimal number of disks per Data Container | 4 |
| Max raw capacity per Data Container | up to 132TB |

NexentaEdge DevOps licensing limitations:

| Resource | Limit |
|------------|-------|
| Max Total Logical Used Capacity (*)| 16TB |
| Max Number of Data Containers | 4 |
| Max Number of GW Containers | Unlimited |

(*) Logical Used Capacity is what application logically allocates. Example would be: iSCSI LUN of 1TB would allocate 1TB of logical. The other example would be: while total raw capacity of 4 servers is 256TB it is still possible to install software with DevOps license initially and then later convert it to unlimited Enterprise (try and then buy model)
