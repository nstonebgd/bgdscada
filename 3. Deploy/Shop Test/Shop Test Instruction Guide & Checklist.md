# Shop Test Instruction Guide & Checklist

## Preparations Before Shop Test

1. **Obtain Necessary Items:**
   - **License Key for HMI:** Secure the license key needed to for the HMI graphics software. This is typically provided by the panel builder but may vary based on the project. Refer to requirements in the projects I&C specifications. 
   - **Cellular Modem:** Ensure cell modem is being provided by panel builder or acquire cell modem based on project requirements. 
   - **SIM Card for Cell Modem:** Bring an unactivated SIM card to place in the cell modem.  
2. **Prepare a USB Drive:**
   - Download Essential Software:
     - [VTScada](https://www.vtscada.com/download-vtscada/)
     - [RealVNC](https://www.realvnc.com/en/connect/download/vnc/)
     - [Wireguard](https://www.wireguard.com/install/)
   - PLC and HMI Programs:
     - PLC Program should have PLC hardware configuration and I/O mapping based on the control panel submittal.
     - HMI program should have register mapping based on control panel submittal.
     - Ensure these programs compile without any errors before saving to USB and project folder. 

## Shop Test Procedures

### 1. Take Pictures of the Control Panel

- **Exterior Panel Door:** Capture the full view and details.

- **Interior Panel Door:** Include both wide-angle and close-up shots.

- **Internal Panel Components:** Ensure clear visibility of all components.

- Model Numbers:

   Focus on the following:

  - PLC
  - PLC I/O cards
  - Cell modem (IMEI and model number)
  - HMI model number
  - Ethernet Switch model number
  - Other Ethernet devices

- **Verification:** Confirm all devices shown on plans and submittals are present.

### 2. Assign IP Addresses

- **General Addressing:** IP addresses should be in the form of 192.client.project.device
  - Modem: 192.client.project.X
  - PLC: 192.client.project.10X
  - PC: 192.client.project.20X
- **PLC Addressing:** Assign an IP in the format 192.client.project.device (e.g., 192.123.45.102 for PLC at Site 2 of project 123-0045). Ensure the PLC Gateway is set to the IP address of the Cell Modem (192.123.45.2 for example)
- **PC Addressing:** Assign a .200 address (e.g., .202 for panel PC at Site 2).

### 3. Install Software

- **VTScada**
- **RealVNC**
- **Wireguard**

### 4. Download Hardware Configuration to the PLC

- **Verification:** Ensure hardware matches the submittal.
- **Error Check:** Confirm no errors in the hardware configuration after download. All lights should be solid green instead of flashing red. 

### 5. Configure PLC Downloading Register Mapping

- **Connection:** Connect to the PLC and download register mapping.
- **Integration:** Include only tag names for all physical I/O in the register map.
- **VTScada Update:** Add register mapping to VTScada.

### 6. Begin I/O Checkout

- **Process:** Test all I/O points based on control panel drawings.
- **Testing Method:** Prefer testing at the furthest point (e.g., switch, push button) over forcing relays.
- **Analog Inputs:** Check signals on analog input cards, including zero signals indicating correct wiring.
- **Simulation:** Have the panel builder simulate 25%, 50%, 75%, 100% 4-20ma signal.
- **Analog Outputs:** Verify visibility of 4-20ma output at corresponding steps.
- **Consistency:** Ensure all I/O matches on both the PLC and the HMI.

### 7. Panel PC Configuration

- **Automatic Power On:** Set the panel PC to automatically power back on after power loss. [Bios setup guide link to be added]
- **Auto-Logon:** Ensure the panel PC is set to auto-logon. [Auto-login guide link to be added]
- **VTScada Auto-Start:** Set VTScada to automatically start on reboot. [VTScada guide link to be added]
- **RealVNC and Wireguard Setup:** Set up RealVNC and Wireguard. [Guide links for each to be added]

### 8. Document Shop Test

- **Record Keeping:** Save all pictures and documentation to the project folder.

**Note:** This guide can be expanded or modified as per specific project requirements or technological updates. Always adhere to safety protocols and standard operating procedures during shop tests.