# Building an IPsec VPN

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to configure an IPsec VPN tunnel to securely transmit data between two endpoints over an untrusted network. The focus is on confidentiality, integrity, and authenticity using a site-to-site VPN configuration.

## Tools Used  
- Linux (Ubuntu/Debian-based)  
- `strongSwan` IPsec VPN software  
- Two virtual machines or cloud instances (on separate networks)  
- Terminal access with `sudo` privileges

## Procedure  

- Install strongSwan on both endpoints:
  ```bash
  sudo apt update
  sudo apt install strongswan
- Configure the IPsec settings on each host:
  - Edit ```/etc/ipsec.conf```:
    ```bash
    config setup
      charondebug="ike 2, knl 2, cfg 2, net 2, esp 2, dmn 2,  mgr 2"

    conn vpn-tunnel
      auto=start
      left=192.168.1.1        # Local IP
      right=192.168.2.1       # Remote IP
      leftid=@left
      rightid=@right
      authby=secret
      ike=aes256-sha1-modp1024!
      esp=aes256-sha1!
      keyexchange=ikev2
      type=tunnel
      leftsubnet=192.168.1.0/24
      rightsubnet=192.168.2.0/24
- Add shared secrets to ```/etc/ipsec.secrets```:
    ```bash
    @left @right : PSK "MyStrongSecret"
- Restart the IPsec service:
    ```bash
    sudo systemctl restart strongswan
- Verify the VPN tunnel:
    ```bash
    ipsec statusall
- Test secure communication:
  - Ping from one subnet to the other
  - Run ```tcpdump``` on both sides to confirm encrypted ESP packets

## Results
- IPsec tunnel successfully established between two isolated networks
- StrongSwan encrypted traffic using AES-256 and SHA1 for integrity
- Secure communication validated by successful ping and encrypted packet flow
- Tunnel automatically re-established after restart or drop

## Lessons Learned
- IPsec provides strong encryption and is widely supported across enterprise networks
- Configuration requires accurate IP mapping, authentication, and subnet planning
- Tools like strongSwan make it possible to build secure site-to-site tunnels in virtual labs
- VPN testing is a critical part of securing enterprise network boundaries
