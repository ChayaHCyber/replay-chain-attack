# Man-in-the-Middle (MitM) & Replay Attack on SCADA Systems
Final project demonstrating a replay attack chain with a live demo (SCADA Traffic Light System)

<a href="https://youtu.be/2kqJ-zq2G0s" target="_blank">
  <img
    width="800"
    height="1080"
    alt="Project"
    src="https://github.com/user-attachments/assets/9661f876-a9bc-4448-a237-017d9903c746"
  />
</a>

## 📖 Project Overview
This project demonstrates a **Man-in-the-Middle (MitM)** attack targeting a simulated **SCADA system**. The setup involves a **Raspberry Pi** acting as a PLC/Controller for a physical traffic light (LED-based), and a **Dockerized client** sending control commands.

By performing **ARP Spoofing**, I intercepted the communication between the HMI (Client) and the field device (Raspberry Pi). I then analyzed the protocol and executed a **Replay Attack** to disrupt the traffic light logic, causing a physical malfunction.

## 🛠️ Infrastructure & SCADA Setup
*   **Field Device (Server):** Raspberry Pi (Running SCADA service on `192.168.1.150`)
*   **HMI/Client:** Docker Container (Host IP `192.168.1.105`)
*   **Attacker:** Kali Linux (ARP Spoofing & Traffic Injection)
*   **Control Hardware:** Custom LED Traffic Light interfaced via GPIO.

  <img width="800" height="1080" alt="Screenshot 2026-02-04 133509" src="https://github.com/user-attachments/assets/d185f2c3-d02f-4fdf-8b4b-2ea95eb199bc" />


## 🚀 Attack Methodology (ICS/SCADA Focus)
1.  **ARP Poisoning:** Redirected traffic between the HMI and the Controller to the attacker machine.
2.  **Traffic Analysis (Wireshark):** Deep packet inspection of the SCADA control protocol to identify "Green/Red" state commands.
3.  **Command Injection & Replay:** Re-injected legitimate control packets repeatedly. This overrode the intended logic, demonstrating how unauthenticated SCADA protocols can be manipulated to cause physical disruption.

## 💡 Industrial Security Takeaways
This project highlights the critical need for encryption and authentication in **Industrial Control Systems (ICS)**. It proves that even without sophisticated exploits, simple network-level attacks can compromise the safety and reliability of physical infrastructure.
