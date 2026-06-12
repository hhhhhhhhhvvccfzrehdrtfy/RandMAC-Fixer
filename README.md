# RandMAC

RandMAC is a Windows Wi-Fi MAC randomization repair and switching tool built for stubborn adapters that refuse to work with normal MAC spoofing tools.

Most MAC spoofing tools try to change the adapter address directly. That works for some Ethernet cards and older adapters, but modern Windows Wi-Fi is different. On many Wi-Fi adapters, especially newer Realtek cards, Windows uses its own randomization system through WLAN profiles, interface GUIDs, and WlanSvc registry state. If any of those layers get stuck, the driver may claim “MAC Randomization: Enabled” while Windows still refuses to actually randomize the address.

RandMAC was created after a real case where a Realtek 8852BE-VT Wi-Fi adapter would not spoof through normal methods. Windows showed MAC randomization as disabled, the profile had randomization off, and standard spoofing tools could not force the router-facing MAC address to change. After testing the Windows WLAN system, driver state, Wi-Fi profiles, registry keys, and adapter GUIDs, the working fix was found: target the active Wi-Fi interface GUID, repair the WlanSvc randomization state, enable daily randomization on the connected Wi-Fi profile, reconnect, and verify the address actually changed.

That is what RandMAC automates.

RandMAC can scan the active Wi-Fi interface, display the current adapter GUID, show the current MAC address, check Windows’ MAC randomization status, back up relevant registry and Wi-Fi profile data, enable randomization for the active Wi-Fi interface, switch the randomized MAC, reconnect Wi-Fi, and verify whether the MAC actually changed. Instead of blindly claiming success, RandMAC compares the old and new MAC addresses and reports whether the switch worked.

The tool is designed for privacy, troubleshooting, and research on devices you own or are allowed to manage. It can help when Windows gets stuck using the permanent hardware MAC even though randomization should be available. It is especially useful for cases where the issue is not the network adapter itself, but Windows applying randomization settings to the wrong or outdated Wi-Fi interface state.

RandMAC does not include driver hacking, unsigned driver installation, kernel drivers, or INF modification. The public release focuses on the clean method that worked: Windows WLAN randomization repair through the current active Wi-Fi GUID and saved Wi-Fi profile settings.

Main features:

* Scan active Windows Wi-Fi adapter information
* Detect the current Wi-Fi interface GUID
* Display the current router-facing MAC address
* Check whether Windows MAC randomization is enabled
* Enable randomization for the active interface
* Set the current Wi-Fi profile to daily randomization
* Switch to a new randomized MAC address
* Disconnect and reconnect Wi-Fi automatically
* Verify old MAC vs new MAC
* Create backups before making changes
* Export reports with privacy-conscious redaction options

RandMAC is not meant to be a ban evasion tool or a way to abuse networks. It is a repair utility for Windows Wi-Fi randomization problems, intended for legitimate privacy, testing, and troubleshooting on your own computer.

The original test case successfully changed a Realtek 8852BE-VT adapter from its permanent hardware MAC to a randomized Windows Wi-Fi MAC after normal spoofing tools failed.

Built by Chase Flood with development and troubleshooting assistance from ChatGPT.
