1. Install Libreswan
    ```
    yum install -y libreswan
    ```

2. Generate an RSA key pair on each host
    ```
    ipsec newhostkey
    ```
    
    Sample output
    ```
    Generated RSA key pair with CKAID XXXXXXX
    ```
    
3. On the first host, display the leftrsasigkey with the CKAID we generated in previous step
    ```
    ipsec showhostkey --left --ckaid XXXXXXX
    ```
    
4. On the second host, display the rightrsasigkey with the CKAID we generated in previous step
    ```
    ipsec showhostkey --right --ckaid XXXXXXX
    ```
    
5. Use showhostkey to list exist keys
    ```
    ipsec showhostkey --list
    ```
    
6. Create and edit a configuration file in /etc/ipsec.d/ipsec-01.conf
    ```
    conn tunnel-name
        leftid=@host1-tunnel-id
        left=host1-IPaddress
        leftrsasigkey=host1-leftrsasigkey
        rightid=@host2-tunnel-id
        right=host2-IPaddress
        rightrsasigkey=host2-rightrsasigkey
        authby=rsasig
    ```
    
7. Restart the IPsec service
    ```
    systemctl restart ipsec
    ```
    
8. Load the VPN tunnel
    ```
    ipsec auto --add tunnel-name 
    ```

9. Bring up the VPN tunnel connection
    ```
    ipsec auto --up tunnel-name
    ```

10. Add below line to start the tunnel automatically when IPsec service is started
    ```
    auto=start
    ```

11. Start IPsec service when system boot.
    ```
    systemctl enable ipsec
    ```
