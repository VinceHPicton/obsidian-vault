A Media Access Control address is a **globally unique** identifier which is assigned to a [[Network cards|NIC]] at the *hardware level*. MAC addresses are burned onto the NIC when they are manufactured.

It is possible to change the MAC address of a NIC at the software level, the OS will override the MAC address, and this change will be reset after the system is shut down, at which point the NIC will still have it's hardware level MAC address.

They look like:
8A:3F:B2:7C:91:E5
c0:6:c3:ac:50:82
ae:81:88:ce:d9:fe

run `arp -a`
On mac/UNIX to see discoverable devices on your local network
