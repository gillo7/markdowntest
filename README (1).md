<!-- form:hide -->
> [!IMPORTANT]
> **Don't answer the questions here.** Open the interactive version:
> 👉 **https://gillo7.github.io/markdowntest/**
>
> Type your answers in the boxes, then click **Download answers** before you leave.
> Lab machines wipe your browser at logout — no export, no answers.
<!-- /form:hide -->

# Lab 1 — Launching and securing an EC2 instance

In this lab you will launch an Ubuntu instance in AWS Academy Learner Lab, connect to it over SSH, and work with its security group.

## C.1 Connecting to your instance

Launch the instance, then open the **Connect** page and copy the SSH command.

```bash
ssh -i "aws_ubuntu_keys.pem" ubuntu@<public-dns>
```

> **Q1.** From your local host, can you ping the public IP address? [Yes/No]

> **Q2.** Why can't you successfully ping your instance?

> **Q3.** Which region of the world is your instance running in?

## C.2 Enabling ICMP on the firewall

Click on the **Security** tab of the instance summary, and then on the security group.

> **Q4.** What is the firewall rule that is applied to the instance?
> [SSH/Telnet/FTP/HTTP/HTTPS] for [0.0.0.0/0 or 0.0.0.0/8 or 0.0.0.0/16 or 0.0.0.0/32]

> **Q5.** What does 0.0.0.0/0 represent?

Now add an ICMP rule for all hosts and try the ping again.

> **Q6.** Your instance has two IP addresses. Why can't you reach it from home using the `172.31.x.x` one?

## C.3 Installing a web server

```bash
sudo apt update
sudo apt install -y apache2
sudo systemctl enable --now apache2
```

> **Q7.** Which port and protocol must you allow in the security group to view the page from your browser?
