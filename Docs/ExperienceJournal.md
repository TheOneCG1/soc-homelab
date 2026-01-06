Day 1: Journal 

Goal:
My goal for today was to create a home lab that would allow me to simulate and train for real-world cybersecurity and SOC scenarios.

Work Performed:
Using three different ISO images, I created three virtual machines to simulate a basic network environment:

SOC Server (soc-server): Intended to act as a centralized monitoring and analysis system.

Windows Endpoint (windows-endpoint): Simulating a user device within the network.

Attacker Machine (ubuntu-attacker): Simulating a potential threat actor system.

I used VMware as the hypervisor to host and manage these virtual machines.

Understanding that a SOC analyst often needs to access systems remotely, I enabled SSH on the SOC server. This allows the Ubuntu attacker machine to establish remote connections for testing purposes and enables remote administration of the SOC server.

Before proceeding further, I verified network connectivity for each virtual machine by pinging 8.8.8.8. All three VMs successfully sent and received packets, confirming that they were connected to the internet.

Outcome:
All three virtual machines were successfully created and verified for basic connectivity.

Next Steps:
On Day 2, I will continue exploring the capabilities of these virtual machines, focusing on endpoint activity, remote access behavior, and system interaction.

Day 2 - 6: 

Days 2–6 – Windows Endpoint VM Exploration & Snapshot Testing

Goal:
My goal during Days 2–6 was to become more familiar with virtual machines, with a specific focus on the Windows endpoint, as this represents what a typical user system would look like in a real-world environment.

Work Performed:
To evaluate the capabilities and limitations of my Windows VM, I performed a series of realistic user activities. I downloaded and installed an application (DVDStyler), ran and operated the software, and tested exporting data by creating an ISO file intended for DVD burning.

During this process, I:

Downloaded external video content (a movie I created and uploaded to YouTube).

Used DVDStyler to design DVD menus.

Generated an ISO file for removable media creation.

Operated entirely within the Windows endpoint virtual machine.

Challenges Encountered:
Using a VM introduced several challenges, particularly during media authoring:

DVDStyler lacked certain playback control buttons within the VM environment.

Menu previews were not viewable in VLC as expected.

Long-running processes, such as DVD burning, were interrupted when the system entered sleep mode.

Key Observations:

DVD authoring generates multiple system artifacts, including:

Cache files

Temporary directories

Output folders

Media authoring tools interact heavily with:

File system permissions

Directory structures

Large file write operations

The Windows endpoint VM was capable of handling resource-intensive tasks with the current configuration.

Creating ISO files and removable media highlights potential data exfiltration vectors.

SOC Relevance:
From a SOC perspective, this activity demonstrated realistic endpoint behavior that analysts must distinguish from malicious actions. Legitimate user behavior can generate high volumes of file system activity that may appear suspicious without proper context. This testing reinforced the importance of baselining normal endpoint activity.

Snapshot & Recovery Testing:
At the conclusion of testing, I used a VM snapshot to restore the Windows endpoint to its original state prior to installing DVDStyler. This demonstrated the effectiveness of snapshots for system recovery and reinforced the importance of backups and rollback capabilities in incident response scenarios.

Outcome:
These exercises provided hands-on experience with endpoint behavior, artifact generation, and system recovery within a virtualized environment.