EBS volumes are characterized by size, throughput (this is MB/s - data transfer rate) and IOPS (in/out ops per sec)

**General purpose (gp) series - cost effective low latency**

*Suitable for boot volumes for EC2 (stores OS files etc) - max **16000 IOPS***
1. gp2: older version, IOPS and throughout are linked, you **do** have to increase IOPS to increase throughput (think adding more ops of 4 KB per second increases throughput)
2. gp3 newer version, completely independently change IOPS and throughput - you **do not** have to increase IOPS to increase throughput

**Provisioned IOPS SSD - highest performance, lowest latency**
*if you need more than 16000 iops, or best latency, supports [[EBS multi-attach]]*
1. io1 - higher performance than general purpose, **max 64000 IOPS (w EC2 nitro), 32000 IOPS otherwise**
2. io2 block express - the best and most expensive one, suitable for very low latency requirements, **max 256,000 IOPS**
**Important points**: 
- If you want over 32000 IOPS in io1, you need **EC2 nitro with io1 or io2**
- If you want over 256,000 IOPS, only an **instance store** can achieve this, you could create a snapshot from the instance store later

**HDD series - low performance, low cost, not for EC2 root volumes**
1. st1 - log processing
2. sc1 - lowest cost EBS available 
