# RandMAC ⚡

RandMAC is a Windows Wi-Fi MAC randomization repair and switching tool built for the adapters that refuse to cooperate.

Most MAC spoofing tools try the obvious route: change the adapter’s MAC address directly and hope Windows listens. That works sometimes, but modern Windows Wi-Fi is messier than that. On newer adapters, Windows uses its own randomization system through WLAN profiles, interface GUIDs, WlanSvc registry state, and adapter-specific driver support. If even one of those layers gets stuck, your driver can say “MAC Randomization: Enabled” while Windows still refuses to actually change the router-facing MAC.

RandMAC was built to attack that exact problem.

Instead of blindly writing a fake MAC and pretending it worked, RandMAC checks the live Wi-Fi interface, finds the current active Windows Wi-Fi GUID, repairs the hidden WlanSvc randomization state, enables randomization on the saved Wi-Fi profile, reconnects the network, and verifies whether the MAC actually changed.

No guessing. No fake success message. RandMAC checks the old MAC against the new MAC and tells you if the switch worked.

## Why RandMAC exists

Some adapters, especially stubborn modern Wi-Fi cards, can fail with normal MAC spoofing tools. Windows may show randomization as disabled, blocked, or stuck even when the driver claims it supports the feature. In some cases, the issue is not the hardware itself. The real problem is that Windows is applying randomization settings to the wrong or outdated Wi-Fi interface state.

RandMAC focuses on the layer most tools ignore:

**Windows’ hidden Wi-Fi GUID randomization state.**

That is what makes it different from a normal MAC spoofer.

## Features

* Scan the active Windows Wi-Fi adapter
* Detect the current Wi-Fi interface GUID
* Show the current router-facing MAC address
* Check Windows MAC randomization status
* Enable randomization for the active Wi-Fi interface
* Set the connected Wi-Fi profile to daily randomization
* Switch to a new randomized MAC
* Disconnect and reconnect Wi-Fi automatically
* Verify old MAC vs new MAC
* Create backups before making changes
* Export privacy-conscious reports
* Avoid risky driver hacking or unsigned driver installs

## What RandMAC is for

RandMAC is designed for privacy, troubleshooting, and research on devices you own or are allowed to manage. It can help when Windows gets stuck using the permanent hardware MAC even though Wi-Fi randomization should be available.

Good uses include:

* Privacy on trusted or public Wi-Fi
* Fixing broken Windows randomization
* Testing router/DHCP behavior
* Researching adapter behavior
* Troubleshooting stubborn Wi-Fi drivers

RandMAC is not built for network abuse, ban evasion, or unauthorized access. Use it responsibly.

## The core idea

Normal tools often target the adapter.

RandMAC targets the Windows Wi-Fi randomization system:

1. Find the active Wi-Fi adapter
2. Find the current Wi-Fi GUID
3. Repair WlanSvc randomization values
4. Enable profile-level randomization
5. Reconnect Wi-Fi
6. Verify the MAC actually changed

If Windows was stuck because of a stale or broken randomization state, RandMAC can bring it back to life.

## Built different ⚡

RandMAC was created after a real-world troubleshooting case where normal spoofing tools failed, Windows claimed randomization was blocked, and the adapter refused to change through the usual methods. The working fix came from tracing the problem through Windows profiles, registry state, adapter GUIDs, and actual MAC verification.

The result is a tool built for the annoying edge cases — the ones where the normal buttons do nothing.

Built by Creator with development and troubleshooting assistance from ChatGPT.
