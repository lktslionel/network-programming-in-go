# Network Fundamentals

## Network topology

**Network topology** A organization of nodes in a network.

There are 6 basic topology catageory:

* **Point-to-point**: Direct connection btw 2 nodes 
  ```
  (o) -> (o)
  ```
* **Dasiy Chain**: A series of P2P connections 
  ```
  (o) -> (o) -> (o) -> (o)
  ```
* **Bus**: All nodes share the same link. All nodes receive the traffic but some could ignore it.
  ```
  (o)    (o)    (o)
   |      |      |
  ---------------------
       |       |
      (o)     (o)
  ``` 
* **Ring**: It is a closed loop; data travel in a single direction
  ```
      (o) -- (o)
    /            \
  (o)             (o)
    \            /
      (o) -- (o)
  ```
* **Star**: A central node as individual P2P connections with all other nodes
  ```
      (o)      (o)
        \     /
  (o) --  (o) -- (o)
        /     \
      (o)      (o)

  ```


* **Mesh**: Every node is connected with every other node in a fully connected mesh.
  ```
      (o)  ---   (o)
    /  |  \   x   | 
  (o) --- (o) -- (o)
    \  | /    x   | 
      (o)  ---   (o)

  ``` 

When you combine multiple topologies, you end up with an hybrid topology.
* Star-Ring
* Star-Bus


## Bandwidth vs Latency

**Bandwidth** is a amount of data we can send over a network connection in an interval of time. 
**Latency** is a measure of the time that passes btw sending a network resource req and receiving a response.

> So you should not focus on bandwidth only, but you should pay attention to Lantency too.


<br>

## OSI

**O**pen **S**ystem **I**nterconnection reference model.

```
  ┌─────┬────────────────────────────┐
  │ L7  │     Application            │ Retrieving resources and identifying hosts
  ├─────┼────────────────────────────┤
  │ L6  │     Presentation           │ Encryption/Decryption/Data Encoding
  ├─────┼────────────────────────────┤
  │ L5  │     Session                │ Manage connection lifecycle
  ├─────┼────────────────────────────┤
  │ L4  │     Transport              │ Transport control (Errors, speed, chunking)
  ├─────┼────────────────────────────┤
  │ L3  │     Network                │ Routing, Addressing, Multicasting, Traffic control
  ├─────┼────────────────────────────┤
  │     │          Logical Link Ctrl │ Data transfert btw 2 directly connected nodes
  │ L2  │ Datalink ------------------│
  │     │          Media Access Ctrl │
  ├─────┼────────────────────────────┤
  │ L1  │     Physical               │ Converts bits to electrical signals
  └─────┴────────────────────────────┘
```

* Network transmission rate is measured in `bits/sec`
* Data  transmission rate is measured in `bytes/sec`

>**Caution**
> `100Mbps` download rate means that you can transfert `100/8 = 12MB/s` over that connection.


<br>

## Data encapsulation
Encapsulation is a means of creating an envelope that hide the content (payload/SDU Service Data Unit) and make only relevant details available to the recipient.

```
 ┌────┬──────────────────────────────┐
 │ L7 │ H7|Request                   │
 ├────┼──────────────────────────────┤
 │ L6 │ H6|H7|Request                │
 ├────┼──────────────────────────────┤
 │ L5 │ H5|H6|H7|Request             │
 ├────┼──────────────────────────────┤
 │ L4 │ UDP/TCP|H5|H6|H7|Request     │ Segment / Datagram
 ├────┼──────────────────────────────┤
 │ L3 │ IP|TCP|H5|H6|H7|Request      │ Packet
 ├────┼──────────────────────────────┤
 │ L2 │ MAC|IP|TCP|H5|H6|H7|Req|FCS  | Frame — FCS: Frame Check Sequence
 ├────┼──────────────────────────────┤
 │ L1 │ 100111011101111010101110001  │ Bit
 └────┴──────────────────────────────┘
```


<br>

## TCP/IP Model

A simplify version of the OSI model.
> TCP/IP doesn’t define specific presentation or session functions. Instead, the specific application protocol implementations concern themselves with those details.

```
 ┌──────────────────────┬──────┐
 │                      │  L7  │
 ├                      ┼──────┤
 │  Application         │  L6  │ HTTP / FTP / SMTP / DHCP / DNS
 ├                      ┼──────┤
 │                      │  L5  │
 ├──────────────────────┼──────┤
 │  Transport           │  L4  │
 ├──────────────────────┼──────┤
 │  Internet / Network  │  L3  │
 ├──────────────────────┼──────┤
 │                      │  L2  │
 ├  Link                ┼──────┤
 │                      │  L1  │
 └──────────────────────┴──────┘
```