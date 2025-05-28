# 🚗 Vehicle CAN Bus Security Simulation

This project was developed as part of CSE 825: Computer and Network Security at Michigan State University. The goal was to simulate and analyze cyberattacks on a virtual Controller Area Network (CAN) bus to understand vulnerabilities in vehicular communication systems and explore practical defense strategies.

---

## 🎯 Objectives

- Simulate a virtual CAN bus using Python
- Demonstrate realistic vehicle cyberattacks:
  - DoS (Flooding the bus)
  - MitM (Modifying intercepted messages)
  - Replay (Reinjection of captured messages)
- Observe and analyze the impact of each attack
- Learn about CAN-based vulnerabilities and propose mitigations

---

## 🧠 Key Concepts

| Attack Type | Behavior | Real-World Impact |
|-------------|----------|-------------------|
| **DoS**     | Floods the CAN bus with high-priority messages | Delays/suppresses critical vehicle functions like braking or steering |
| **MitM**    | Intercepts and modifies legitimate messages | Falsifies sensor/control data (e.g., disabling airbags, spoofing speed) |
| **Replay**  | Reinjects previously captured messages | Causes redundant or unintended vehicle behavior (e.g., door unlocking) |

---

## 🛠️ Technologies Used

- Python 3
- `threading` module
- `queue.Queue` for simulating the CAN bus
- No physical hardware required (fully virtual simulation)

---

## 🧪 How It Works

- Each node (sender, receiver, attacker) is simulated using a separate Python thread.
- Messages are passed through a shared `Queue` that represents the CAN bus.
- Attackers operate concurrently, injecting malicious messages alongside legitimate traffic.

---

## 🐍 Example Output Snippet

```text
Sender: Sent ID: 0x123, Data: [113, 190, 31, 190]
Receiver: Received ID: 0x123, Data: [113, 190, 31, 190]
Attacker (DoS): Flooded ID: 0x7ff, Data: [0, 0, 0, 0, 0, 0, 0, 0]
Attacker (MitM): Intercepted ID: 0x123, Data: [...]
Attacker (MitM): Injected ID: 0x123, Data: [255, 255, 255, 255]
Attacker (Replay): Replayed ID: 0x123, Data: [...]
✅ Proposed Mitigations
Attack	Mitigation
DoS	Rate-limiting, message prioritization, IDS
MitM	Encryption, authentication, MACs
Replay	Timestamps, sequence counters, nonces

📂 Files
CAN Bus with Attacks.ipynb: Jupyter Notebook simulating the CAN environment and attacks

📌 Lessons Learned
Simulating concurrency and message priority is key in emulating CAN logic.

Even a virtual CAN system demonstrates how real-world vehicle systems can be compromised.

Thread synchronization and message logging are critical for monitoring attack impact.

🔒 Disclaimer
This simulation is for educational purposes only. Do not use the techniques learned here on real vehicles or production environments.

