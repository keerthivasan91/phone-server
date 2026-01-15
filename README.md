# Phone-Based Web Server (Termux + Flask)

This is a small **hobby learning project** where an Android phone is used as a lightweight Linux web server using **Termux**. A simple **Flask** application runs locally on the phone and is securely exposed to the internet using **Cloudflare Tunnel**.

The purpose of this project is to understand basic **server setup, SSH access, networking, and tunneling concepts**. This is not intended for production use.


## Tech Stack
- Android
- Termux (Linux environment)
- Python
- Flask
- SSH
- Cloudflare Tunnel


---

## Project Structure
```
phone-server-project/
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
└── screenshots/
```

---

## How It Works
1. Termux provides a Linux environment on the Android phone  
2. Flask runs a web app locally on `127.0.0.1:5000`  
3. SSH is used to access the phone from a laptop  
4. Cloudflare Tunnel exposes the local app securely over HTTPS  
5. No router port forwarding or public IP exposure is used  

---
# How to Set Up This Project

## 1. Install Termux
Install **Termux** from Play store and update packages:
```bash
pkg update && pkg upgrade
```

## 2. Install Required Packages
```bash
pkg install python git openssh
pip install -r requirements.txt
```

## 3. Start the Flask App
```bash
python app.py
```
The app will run locally on `http://127.0.0.1:5000`.

## 4. Expose the App Using Cloudflare Tunnel
Install cloudflared and start a quick tunnel:
```bash
cloudflared tunnel --url http://localhost:5000
```
A public HTTPS URL will be generated.

## 5. (Optional) SSH Access from Laptop
Start SSH on the phone:
```bash
sshd
```

Connect from laptop:
```bash
ssh -p 8022 username@phone_ip
```

## Security Notes
- Flask is bound to localhost only
- Debug mode is disabled
- SSH key-based access is used
- HTTPS is handled by Cloudflare Tunnel
- No inbound ports are opened on the router

---

## Limitations
- Phone battery and uptime dependent
- Temporary tunnel URL
- Not suitable for production deployment

---
## ScreenShot

![image](https://github.com/user-attachments/assets/d03778ff-13bb-42da-975e-f680f66e0d12
)
