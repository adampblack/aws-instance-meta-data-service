
<a name="top"></a> 
# AWS instance meta data service

Reference: [AWS User Guide - Instance data retrieval]( https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-data-retrieval.html)

Contents:
- [Versions](#versions)
- [Options](#options)
- [Amazon machine image (AMI) ID](#ami_id)
- [Amazon machine image (AMI) launch index value](#ami_launch_index)
- [Amazon manifest path](#amazon_manifest_path)
- [Block device mapping](#block_device_mapping)
- [Events](#events)
- [Hostname](#hostname)
- [IAM](#iam)
- [Instance action](#instance_action)
- [Instance ID](#instance_id)
- [Instance life cycle](#instance_life_cycle)
- [Instance type](#instance_type)
- [Local hostname](#local_hostname)
- [Local IP4](#local_ip4)
- [MAC address](#mac_address)
- [Metrics](#metrics)
- [Network](#network)
- [Placement](#placement)
- [Profile](#profile)
- [Public hostname](#public_hostname)
- [Public IP4](#public_ip4)
- [Public keys](#public_keys)
- [Reservation ID](#reservation_id)
- [Security groups](#security_groups)
- [Services](#services)

---

<a name="versions"></a> 
## Versions

According to the AWS documentation, "the earlier versions are available to you in case you have scripts that rely on the structure and information present in a previous version."

```bash
curl http://169.254.169.254/
```

```bash
1.0
2007-01-19
2007-03-01
2007-08-29
2007-10-10
2007-12-15
2008-02-01
2008-09-01
2009-04-04
2011-01-01
2011-05-01
2012-01-12
2014-02-25
2014-11-05
2015-10-20
2016-04-19
2016-06-30
2016-09-02
2018-03-28
2018-08-17
2018-09-24
2019-10-01
2020-10-27
2021-01-03
```

The way that this would be used.

For the latest:
```bash
curl http://169.254.169.254/latest/meta-data/
```

For a specific version (e.g. 2021-01-03):
```bash
curl http://169.254.169.254/2021-01-03/meta-data/
```

[[Back to top]](#top)

---

<a name="options"></a>
## Options

Using latest version:
```bash
curl http://169.254.169.254/latest/meta-data/
```

```bash
ami-id
ami-launch-index
ami-manifest-path
block-device-mapping/
events/
hostname
iam/
identity-credentials/
instance-action
instance-id
instance-life-cycle
instance-type
local-hostname
local-ipv4
mac
metrics/
network/
placement/
profile
public-hostname
public-ipv4
public-keys/
reservation-id
security-groups
```

[[Back to top]](#top)

---

<a name="ami_id"></a>
## Amazon machine image (AMI) ID

```bash
curl http://169.254.169.254/latest/meta-data/ami-id
```

```bash
ami-07f990e4e7551b774
```

[[Back to top]](#top)

---

<a name="ami_launch_index"></a>
## Amazon machine image (AMI) launch index value

When running up new instances (aws ec2 run-instances) and running up multiple instances of the same AMI (using the count option).

Each instance will be launched with a unique index started from a zero-index (0) and incrementing by 1 for each additional instance.

Reference: [AWS User Guide - Amazon Launch Index](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMI-launch-index-examples.html)

```bash
curl http://169.254.169.254/latest/meta-data/ami-launch-index
```

```bash
0
```
[[Back to top]](#top)

---

<a name="amazon_manifest_path"></a>
## Amazon manifest path

```bash
curl http://169.254.169.254/latest/meta-data/ami-manifest-path
```

```bash
(unknown)
```

[[Back to top]](#top)

---

<a name="block_device_mapping"></a>
## Block device mapping

```bash
curl http://169.254.169.254/latest/meta-data/block-device-mapping/
```

```bash
ami
```

One level deeper:
```bash
curl http://169.254.169.254/latest/meta-data/block-device-mapping/ami
```

```bash
xvda(python3)
```

[[Back to top]](#top)

---

<a name="events"></a>
## Events

```bash
curl http://169.254.169.254/latest/meta-data/events/
```

```bash
maintenance/(python3)
```

One level deeper:
```bash
curl http://169.254.169.254/latest/meta-data/events/maintenance
```

```bash
history
```

One level deeper:
```bash
curl http://169.254.169.254/latest/meta-data/events/maintenance/history
```

```bash
[](python3)
```

[[Back to top]](#top)

---
<a name="hostname"></a>
## Hostname

```bash
curl http://169.254.169.254/latest/meta-data/hostname
```

```bash
ip-123-45-67-89.us-east-1.compute.internal(python3)
```

[[Back to top]](#top)

---
<a name="iam"></a>
## IAM

```bash
curl http://169.254.169.254/latest/meta-data/iam
```

```bash
security-credentials/(python3)
```

One level deeper:
```bash
curl http://169.254.169.254/latest/meta-data/iam/security-credentials
```

```bash
example_iam_role(python3)
```

[[Back to top]](#top)

---
<a name="instance_action"></a>
## Instance action

```bash
curl http://169.254.169.254/latest/meta-data/instance-action
```

```bash
none(python3)
```

[[Back to top]](#top)

---

<a name="instance_id"></a>
## Instance ID

```bash
curl http://169.254.169.254/latest/meta-data/instance-id
```

```bash
i-1234d5bf6f789b123(python3)
```

---
<a name="instance_life_cycle"></a>
## Instance life cycle

```bash
curl http://169.254.169.254/latest/meta-data/instance-life-cycle
```

```bash
on-demand(python3)
```

[[Back to top]](#top)

---
<a name="instance_type"></a>
## Instance type

```bash
curl http://169.254.169.254/latest/meta-data/instance-type
```

```bash
t3.micro(python3)
```

[[Back to top]](#top)

---

<a name="local_hostname"></a>
## Local hostname

```bash
curl http://169.254.169.254/latest/meta-data/local-hostname
```

```bash
ip-172-12-34-56.us-east-1.compute.internal(python3)
```

[[Back to top]](#top)

---

<a name="local_ip4"></a>
## Local IP4

```bash
curl http://169.254.169.254/latest/meta-data/local-ipv4
```

```bash
172.12.34.56(python3)
```

[[Back to top]](#top)

---

<a name="mac_address"></a>
## MAC address

```bash
curl http://169.254.169.254/latest/meta-data/mac
```

```bash
12:3a:c4:a5:c6:d7(python3)
```

[[Back to top]](#top)

---

<a name="metrics"></a>
## Metrics

```bash
curl http://169.254.169.254/latest/meta-data/metrics/
```

```bash
vhostmd(python3)
```

One level deeper:
```bash
curl http://169.254.169.254/latest/meta-data/metrics/vhostmd
```

```bash
<?xml version="1.0" encoding="UTF-8"?>(python3) 
```

[[Back to top]](#top)

---

<a name="network"></a>
## Network

```bash
curl http://169.254.169.254/latest/meta-data/network/
```

```bash
interfaces/(python3)
```

One level deeper:
```bash
curl http://169.254.169.254/latest/meta-data/network/interfaces
```

```bash
macs/(python3)
```

One level deeper:
```bash
curl http://169.254.169.254/latest/meta-data/network/interfaces/macs
```

```bash
12:3a:c4:a5:c6:d7(python3)
```

[[Back to top]](#top)

---

<a name="placement"></a>
## Placement

```bash
curl http://169.254.169.254/latest/meta-data/placement/
```

```bash
availability-zone
region(python3)
```

One level deeper (availability-zone):
```bash
curl http://169.254.169.254/latest/meta-data/placement/availability-zone
```

```bash
us-east-1a(python3)
```

One level deeper (region):
```bash
curl http://169.254.169.254/latest/meta-data/placement/region
```

```bash
us-east-1(python3)
```

[[Back to top]](#top)

---

<a name="profile"></a>
## Profile

```bash
curl http://169.254.169.254/latest/meta-data/profile
```

```bash
default-hvm(python3)
```

[[Back to top]](#top)

---

<a name="public_hostname"></a>
## Public hostname

```bash
curl http://169.254.169.254/latest/meta-data/public-hostname
```

```bash
ec2-123-234-123-234.us-east-1.compute.amazonaws.com(python3)
```

[[Back to top]](#top)

---

<a name="public_ip4"></a>
## Public IP4

```bash
curl http://169.254.169.254/latest/meta-data/public-ipv4
```

```bash
123.234.123.234(python3)
```

[[Back to top]](#top)

---
<a name="public_keys"></a>
## Public keys

```bash
curl http://169.254.169.254/latest/meta-data/public-keys/
```

```bash
0=example_public_key(python3)
```

[[Back to top]](#top)

---

<a name="reservation_id"></a>
## Reservation ID

```bash
curl http://169.254.169.254/latest/meta-data/reservation-id/
```

```bash
r-1d23bb4567f89e1c2(python3)
```

[[Back to top]](#top)

---

<a name="security_groups"></a>
## Security groups

```bash
curl http://169.254.169.254/latest/meta-data/security-groups
```

```bash
example_security_group
```

[[Back to top]](#top)

---

<a name="services"></a>
## Services


```bash
curl http://169.254.169.254/latest/meta-data/services/
```

```bash
domain
partition(python3) 
```

One level deeper (domain):

```bash
curl http://169.254.169.254/latest/meta-data/services/domain
```

```bash
amazonaws.com(python3) 
```

One level deeper (partition):

```bash
curl http://169.254.169.254/latest/meta-data/services/partition
```

```bash
aws(python3)
```

[[Back to top]](#top)
