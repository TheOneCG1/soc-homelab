# **Day 1 – SOC Lab Setup**

**Goal:**
Create a home lab that would allow me to simulate and train for real-world cybersecurity and SOC scenarios.

**Work Performed:**

* Using three different ISO images, I created three virtual machines to simulate a basic network environment:

  * **SOC Server (soc-server):** Centralized monitoring and analysis system.
  * **Windows Endpoint (windows-endpoint):** Simulates a typical user device.
  * **Attacker Machine (ubuntu-attacker):** Simulates a potential threat actor system.
* I used **VMware** as the hypervisor to host and manage these virtual machines.
* Enabled **SSH on the SOC server** to allow remote connections from the Ubuntu attacker machine and enable remote administration of the SOC server.
* Verified network connectivity by **pinging 8.8.8.8** from each VM; all three VMs successfully sent and received packets, confirming internet connectivity.

**Outcome:**
All three virtual machines were successfully created and verified for basic connectivity.

**Next Steps:**
On Day 2, I will explore the capabilities of these virtual machines further, focusing on endpoint activity, remote access behavior, and system interaction.

---

# **Days 2–6 – Windows Endpoint VM Exploration & Snapshot Testing**

**Goal:**
Become familiar with virtual machines, specifically the Windows endpoint, which represents a typical user system in a real-world environment.

**Work Performed:**

* Evaluated the Windows VM by performing realistic user activities:

  * Downloaded and installed **DVDStyler**.
  * Created DVD menus and exported content by generating an **ISO file** for DVD burning.
  * Downloaded external video content (a movie I created and uploaded to YouTube).
* Operated entirely within the Windows endpoint VM.

**Challenges Encountered:**

* DVDStyler lacked certain playback control buttons in the VM environment.
* Menu previews could not be viewed in VLC as expected.
* Long-running processes, such as DVD burning, were interrupted when the system entered sleep mode.

**Key Observations:**

* DVD authoring generates multiple system artifacts:

  * Cache files
  * Temporary directories
  * Output folders
* Media authoring tools interact heavily with:

  * File system permissions
  * Directory structures
  * Large file write operations
* The Windows endpoint VM handled resource-intensive tasks successfully.
* Creating ISO files highlighted potential **data exfiltration vectors**.

**SOC Relevance:**

* Demonstrated realistic endpoint behavior that analysts must distinguish from malicious actions.
* Reinforced the importance of **baselining normal user activity** to identify anomalies.

**Snapshot & Recovery Testing:**

* Used a VM snapshot to restore the Windows endpoint to its original state before installing DVDStyler.
* Demonstrated effective **system recovery** and reinforced the importance of **backups and rollback capabilities** in incident response scenarios.

**Outcome:**
Gained hands-on experience with endpoint behavior, artifact generation, and system recovery in a virtualized environment.

---

# **Day 7 – Setting up Wazuh SIEM on Ubuntu 24**

**Goal:**
Set up a Security Information and Event Management (SIEM) system using the open-source version of Wazuh to simulate SOC operations and manage security events.

**Work Performed:**

1. **Initial Setup:**

   * Running **Ubuntu 24** on the SOC-server VM.
   * Initially attempted to install Wazuh 4.11 but encountered installation issues due to limited documentation and resources.

2. **Successful Installation:**

   * Used the **official Wazuh installer** and the **all-in-one package**.
   * The first failed installation was automatically removed, after which the **Wazuh Manager** was installed successfully.

3. **Network Troubleshooting:**

   * Attempted to access the Wazuh dashboard via **Google Chrome**, but the page did not load.
   * Switched the VM network adapter from **NAT to Bridge mode** to share the same subnet as the host PC.
   * Verified connectivity by **pinging the SOC-server IP** and performing a **port check on 443**, confirming the dashboard port was open.

4. **Dashboard Access:**

   * Using **Safari**, I successfully accessed the Wazuh dashboard.
   * Attempted login with the admin UUID but realized the password had not been saved.

5. **Password Reset:**

   * Accessed hidden directories on the SOC-server using **root privileges**.
   * Navigated to `/usr/share/wazuh-dashboard/bin/` to locate **`wazuh-passwords-tool.sh`**.
   * Executed the tool to **reset the admin password** successfully.

6. **Verification:**

   * Restarted all services (`wazuh-manager`, `opensearch`, `wazuh-dashboard`) to ensure the changes took effect.
   * Successfully logged in to the **Wazuh dashboard**, confirming full functionality.

**Observations / Lessons Learned:**

* **Bridge mode** is essential for VM accessibility from the host machine.
* Browser compatibility can affect dashboard access; Safari worked when Chrome did not.
* Wazuh credentials are stored securely in the **OpenSearch keystore** and cannot be accessed directly.
* Restarting services after configuration changes ensures that all components reflect updates correctly.


