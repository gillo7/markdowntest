# Lab 1 — Launching and securing an EC2 instance

In this lab you will launch an Ubuntu instance in AWS Academy Learner Lab, connect to it over SSH, and work with its security group.

> [!TIP]
> Open a text file for your answers. Paste this at the top, then use the **copy** button on each ❓ question as you reach it.

```text
Name:
Matric:
Lab 1 — Launching and securing an EC2 instance
```

## C.1 Connecting to your instance

Launch the instance, then open the **Connect** page and copy the SSH command:

```bash
ssh -i "aws_ubuntu_keys.pem" ubuntu@<public-dns>
```

<details>
<summary>🔧 Connection timed out?</summary>

- Make sure you're using the **public** IP or DNS name, not the `172.31.x.x` private address.
- Check the security group has an inbound **SSH (22)** rule.
- Uni network blocking port 22? Try a phone hotspot.

</details>

**❓ Question 1**

```text
Q1. From your local host, can you ping the public IP address? [Yes/No]
Answer:
```

**❓ Question 2**

```text
Q2. Why can't you successfully ping your instance?
Answer:
```

**❓ Question 3**

```text
Q3. Which region of the world is your instance running in?
Answer:
```

## C.2 Enabling ICMP on the firewall

Click on the **Security** tab of the instance summary, and then on the security group.

**❓ Question 4**

```text
Q4. What is the firewall rule that is applied to the instance?
[SSH/Telnet/FTP/HTTP/HTTPS] for [0.0.0.0/0 or 0.0.0.0/8 or 0.0.0.0/16 or 0.0.0.0/32]
Answer:
```

**❓ Question 5**

```text
Q5. What does 0.0.0.0/0 represent?
Answer:
```

Now add an ICMP rule for all hosts and check your instance details from the CLI:

```bash
aws ec2 describe-instances --no-cli-pager
```

<details>
<summary>📄 Expected output (shortened)</summary>

```json
{
    "Reservations": [
        {
            "Instances": [
                {
                    "InstanceType": "t2.micro",
                    "State": { "Name": "running" },
                    "PublicIpAddress": "107.23.185.65",
                    "PrivateIpAddress": "172.31.18.160"
                }
            ],
            "OwnerId": "590269919252"
        }
    ]
}
```

</details>

> [!WARNING]
> Stuck on a screen ending in `(END)`? Press **q** to quit the pager.

## C.3 Installing a web server

```bash
sudo apt update
sudo apt install -y apache2
sudo systemctl enable --now apache2
```

**❓ Question 6**

```text
Q6. Which port and protocol must you allow in the security group to view the page from your browser?
Answer:
```
