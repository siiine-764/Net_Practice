# Net_Practice

![NetPractice](https://github.com/siiine-764/Net_Practice/assets/80540449/d587216a-eacc-4df2-8c68-827e12ba92eb)


## Contents
- [Basics](https://github.com/siiine-764/Net_Practice#basics)
  - [special IP-ranges](https://github.com/siiine-764/Net_Practice#special-ip-ranges)
  - [Masks](https://github.com/siiine-764/Net_Practice#masks)
  - [Switches](https://github.com/siiine-764/Net_Practice#switches)
  - [Routers](https://github.com/siiine-764/Net_Practice#routers)
  - [Routing Tables](https://github.com/siiine-764/Net_Practice#routing-tables)
  - [Network](https://github.com/siiine-764/Net_Practice#network)
    
- [Levels](https://github.com/siiine-764/Net_Practice#levels)
  - [Level 1](https://github.com/siiine-764/Net_Practice#level-1)
  - [Level 2](https://github.com/siiine-764/Net_Practice#level-2)
  - [Level 3](https://github.com/siiine-764/Net_Practice#level-3)
  - [Level 4](https://github.com/siiine-764/Net_Practice#level-4)
  - [Level 5](https://github.com/siiine-764/Net_Practice#level-5)
  - [Level 6](https://github.com/siiine-764/Net_Practice#level-6)
  - [Level 7](https://github.com/siiine-764/Net_Practice#level-7)
  - [Level 8](https://github.com/siiine-764/Net_Practice#level-8)
  - [Level 9](https://github.com/siiine-764/Net_Practice#level-9)
  - [Level 10](https://github.com/siiine-764/Net_Practice#level-10)
 
- [Explanation](https://github.com/siiine-764/Net_Practice#Explanation)


## Basics
For this project we only use IPv4, so I won't talk about IPv6.<br>
An IPv4-adress is a 32-bit number divided into 4 "blocks", each 8 bits.<br>
i.e.:<br>
`192.168.100.1` turns into `11000000.10101000.01100100.00000001`<br>
So the min. value of one "block" is `0` and the max. value is `255`.<br>
The same logic applies to the network-mask:<br>
`255.255.255.0` turns into `11111111.11111111.11111111.00000000`<br>
Special to the mask is, after one bit was `0` there can't be any `1` bit's anymore.<br>
So the only available numbers are:


- `255 (binary: 11111111)`
- `254 (binary: 11111110)`
- `252 (binary: 11111100)`
- `248 (binary: 11111000)`
- `240 (binary: 11110000)`
- `224 (binary: 11100000)`
- `192 (binary: 11000000)`
- `128 (binary: 10000000)`
- `0 (binary: 00000000)`


Through which `255.255.255.0` is a valid mask<br>
and `255.255.128.128` is **not** a valid mask.<br>
<br>
In order to have the ability to send packages between two IP-addresses they either need to be part of the same network or they need to be connected by a router which is part of both subnets.

## Special IP-ranges

The following special address-ranges are reserved for Private Networks:<br>
`10.0.0.0 – 10.255.255.255`<br>
`172.16.0.0 – 172.31.255.255`<br>
`192.168.0.0 – 192.168.255.255`<br>

The following address-range is reserved for so called loopback addresses:<br>
`127.0.0.0 – 127.255.255.255`


There is some more special ip-ranges, but for this project, you only need to remember those above.

![website for check IPs](https://www.ipqualityscore.com/ip-reputation-check) <br>

## Masks

The network-mask, subnet-mask or in our project only called mask is there to decide which range of ip-adresses are part of the same subnet.<br>
There are 2 different ways of writing the mask:

- "Dot-decimal notation": `255.255.255.0`
- "Class Inter-Domain Routing" or "CIDR": `/24`


The more usable ip-addresses you need in one subnet, the less subnets you will be able to create.<br>
To help you understanding it, I found this table very helpful:


| CIDR | Dot-decimal | Number of IP-addresses<br /> per subnet | Usable IP-addresses <br /> per subnet | Number of subnets |
| :---: | :-----------: | :---: | :---: | :---: |
| /32 | 255.255.255.255 | 1 | 0 | 256 |
| /31 | 255.255.255.254 | 2 | 0 | 128 |
| /30 | 255.255.255.252 | 4 | 2 | 64 |
| /29 | 255.255.255.248 | 8 | 6 | 32 |
| /28 | 255.255.255.240 | 16 | 14 | 16 |
| /27 | 255.255.255.224 | 32 | 30 | 8 |
| /26 | 255.255.255.192 | 64 | 62 | 4 |
| /25 | 255.255.255.128 | 128 | 126 | 2 |
| /24 | 255.255.255.0 | 256 | 254 | 1 |


The number of usable IP-addresses per subnet is lower than the total number of IP's because the first address is reserved as the network-address of the subnet and the last address is reserved as a broadcast-adress.<br>
i.e. for mask `255.255.255.252`:<br>
network: `190.3.2.252`<br>
broadcast: `190.3.2.255`<br>
usable IP's: `190.3.2.253`, `190.3.2.254`
![subnet-mask-catharsis](https://github.com/siiine-764/Net_Practice/assets/80540449/45457891-7395-48a2-8747-1259d304885f)


- Why does IPv4 need a netmask?

    - Improved Network Security.
  
    - Better Network Performance and Speed.
  
    - Administration is a Breeze.
  
    - Easier to Control Growth of Network.
  
    - Less Network Congestion.

## Switches

A switch will enable you to connect more than two devices to the same network.<br>
Its only purpose is to distribute packages to its network.<br>
To see a working example, you can take a look at <br>
<img width="1138" alt="level3" src="https://github.com/siiine-764/Net_Practice/assets/80540449/45396dc4-edfa-496a-bb0c-6735e1882461">

## Routers
(rule routers : control workflow between tasks in a process)
As previously mentioned a router is an interface which enables communication between different networks.<br>
A router has the ability to be part of multiple networks, in Netpractice this is visualized by the so called `Interface`.<br>
If routers and switches are still magic to you, I suggest looking deeper [into it](https://www.youtube.com/watch?v=Vc16CCAAz7Q) yourself, as their basic understanding is crucial to succeed in this project.

## Routing Table

<img width="100%" alt="router_example" src="https://github.com/siiine-764/Net_Practice/assets/80540449/c99b537b-b386-4a52-bc0b-e68817dbd1e6">
- Routing Table on Windows:

cmd on windows:

    Get-NetRoute -AddressFamily IPv6

cmd on Mac:

    netstat -rn

![Screenshot 2023-07-22 181953](https://github.com/siiine-764/Net_Practice/assets/80540449/98532641-bf77-4139-beb9-d1ba0148f43c)

The routing table is there to store all the different paths to all the networks, the device is part of.<br>
In Net_Practice the routing table consists of two elements, the **destination** and the **next hop**<br>
The **destination** consists of the network-address that you want to send a package to, combined with the CIDR of that network: `190.3.2.252/30`. If you don't want to specify a destination, you can just set it to `default` or `0.0.0.0/0`.<br>
The **next hop** is the address of the next router that you need to send the packages to in order to reach the destination-network.<br>

## Network

And now to connect all of the above mentioned topics.<br>
In order to have a functioning network, you now need to apply all of the parts talked about earlier.<br>
If there should be a working connection in a network, the devices somehow need to be connected, either directly or with the help of routers which are part of both networks.


Now you may ask, how do I know if two devices are part of the same network?<br>
For this you need to combine the IP-address and the mask of the devices in order to get the network-adress, that device is part of.<br>
By combining I mean, doing a bit-by-bit-AND-opperation.<br>
For that we first need to translate the IP and the mask to binary.<br>
i.e.:<br>
IP: `192.168.100.1` in binary: `11000000.10101000.1100100.00000001`<br>
MASK: `255.255.255.0` in binary: `11111111.11111111.11111111.00000000`<br>
Now you just combine the two bit by bit, if both bits are a `1` the corresponding bit of the network-address is `1`, in any other case the corresponding bit is `0`.


By doing that to the mentioned example, you should get the network-address of<br>`11000000.10101000.1100100.00000000` in binary or `192.168.100.0` in dot-decimal.<br>
If two devices share the same network-address, they are part of the same network and communication is ensured.

## Levels

Here are all the solutions and explanations for all 10 Levels.<br>

---

### Level 1

<details>
  <summary>show</summary>
  <img width="1186" alt="level1" src="https://github.com/siiine-764/Net_Practice/assets/80540449/dcc66543-f139-4a59-8fe9-42c6f33cbd46">

  <br>
</details>

---

### Level 2

<details>
  <summary>show</summary>
  <img width="1023" alt="level2" src="https://github.com/siiine-764/Net_Practice/assets/80540449/8977a5c7-03c5-4580-aeb5-1c7c896ba54b">

  <br>
</details>

---

### Level 3

<details>
  <summary>show</summary>
<img width="1138" alt="level3" src="https://github.com/siiine-764/Net_Practice/assets/80540449/45396dc4-edfa-496a-bb0c-6735e1882461">

  
  <br>
</details>

---

### Level 4


<details>
  <summary>show</summary>
  <img width="1254" alt="level4" src="https://github.com/siiine-764/Net_Practice/assets/80540449/2448771e-cc56-4806-a042-d8d3b97a4aa9">

  <br>
</details>

---

### Level 5

<details>
  <summary>show</summary>

<img width="1395" alt="level5" src="https://github.com/siiine-764/Net_Practice/assets/80540449/3b3daca8-9060-466f-82cd-d8648904d3ac">

  
  <br>
</details>

---

### Level 6

<details>
  <summary>show</summary>
  <img width="1478" alt="level6" src="https://github.com/siiine-764/Net_Practice/assets/80540449/d9cc44b4-3493-4a1d-a6e6-b69907ecec97">

  <br>
</details>

---

### Level 7

<details>
  <summary>show</summary>

  <img width="1617" alt="level7" src="https://github.com/siiine-764/Net_Practice/assets/80540449/97755354-a42c-40d0-a65a-c19136771135">

  <br>
</details>

---


### Level 8

<details>
  <summary>show</summary>
<img width="1508" alt="level8" src="https://github.com/siiine-764/Net_Practice/assets/80540449/210ef20c-0b83-40e8-afd1-cb41e3945112">

  
  <br>
</details>

---

### Level 9

<details>
  <summary>show</summary>
<img width="1433" alt="level9" src="https://github.com/siiine-764/Net_Practice/assets/80540449/0b4f6269-0b96-4ea0-9edd-2c5155af1095">

  

  <br>
</details>

---

### Level 10

<details>
  <summary>show</summary>
<img width="1347" alt="level10" src="https://github.com/siiine-764/Net_Practice/assets/80540449/f9051f87-359b-45e9-b73d-4d2497205a8a">

  
  <br>
</details>


### Explanation :

https://miro.com/app/board/uXjVMoh8dFU=/

# Playlist :

https://www.youtube.com/watch?v=5WfiTHiU4x8&list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF

# Practice : 

https://subnetipv4.com/#learn



