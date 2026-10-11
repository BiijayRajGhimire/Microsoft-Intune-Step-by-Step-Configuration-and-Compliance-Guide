# Microsoft-Intune-Step-by-Step-Configuration-and-Compliance-Guide
intune.microsoft.com (Microsoft Intune admin center). Menu names may change slightly as Microsoft updates the portal. Part 1: Configuration Process
Part	Contents
1	Configuration process (6 steps) with flow diagram
2	Compliance process (7 steps) with flow diagram
3	Quick checklist and best practices

Admin portal: intune.microsoft.com (Microsoft Intune admin center). Menu names may change slightly as Microsoft updates the portal. Part 1: Configuration Process
 
Configuration Steps in Detail
1. Prerequisites
-	Get a license that includes Intune (Microsoft 365 E3/E5, Business Premium, EMS, or standalone Intune).
-	Assign licenses to users in the Microsoft 365 admin center.
-	Make sure you hold the Intune Administrator or Global Administrator role.
-	Sign in to the Intune admin center at intune.microsoft.com.
2. Entra ID and domain setup
-	In Entra ID, go to Devices > Device settings and allow users to join or register devices.
-	Under Mobility (MDM and MAM), select Microsoft Intune and set the MDM user scope to All or a pilot group.
-	Apple devices: add an APNs certificate under Devices > Enroll devices > Apple.
-	Android Enterprise: link a managed Google Play account.
3. Enrollment
Platform	Common method
Windows	Windows Autopilot (upload hardware hashes, create a deployment profile), or
Entra join with autoenrollment
iOS / iPadOS / macOS	Apple Business Manager automated enrollment, or User Enrollment for
BYOD
Android	Fully Managed, Work Profile, or Dedicated devices
Optionally set enrollment restrictions and device limits.
4. Groups and filters
-	Create Entra groups, static or dynamic (for example by OS or department).
-	Create a pilot group so you can test before broad rollout.
-	Use assignment filters to target by OS version, model, or ownership.
<img width="1025" height="318" alt="image" src="https://github.com/user-attachments/assets/988debe6-9967-40bc-9a9c-73602756c45a" />
Configuration profiles
-	Go to Devices > Configuration > Create > New policy.
-	Choose the platform and profile type, usually Settings catalog.
-	Configure settings such as Wi-Fi, VPN, BitLocker, Defender, and restrictions.
-	Assign the profile to a group and monitor it under Device status.
<img width="1025" height="385" alt="image" src="https://github.com/user-attachments/assets/c6e0f6b7-d710-430b-9525-aed275f66e01" />
<img width="1025" height="370" alt="image" src="https://github.com/user-attachments/assets/ec65bec8-0c81-4c01-9eba-34b32c687974" />
<img width="1025" height="354" alt="image" src="https://github.com/user-attachments/assets/d7b58f30-90c6-4d97-b7a0-62715af6e68c" />
<img width="997" height="331" alt="image" src="https://github.com/user-attachments/assets/a9e04ebf-7ff2-409c-8f26-6dce49a8e1d7" />
<img width="1025" height="457" alt="image" src="https://github.com/user-attachments/assets/21868dd3-93c0-4da3-8639-0fca92ec1f61" />
<img width="1025" height="468" alt="image" src="https://github.com/user-attachments/assets/9ab1c128-3333-4cef-b43e-7fd7d52da657" />
After saving all setting.
6. Apps and updates
-	Go to Apps > All apps > Add (Microsoft 365 Apps, Store, Win32, LOB, and so on).
-	Assign each app as Required, Available, or Uninstall.
-	Set up Windows Update rings and feature update policies under Devices > Windows > Update rings.
Part 2: Compliance Process
 
Compliance Steps in Detail
1. Set the tenant-wide compliance policy settings
-	Go to Devices > Compliance > Compliance policy settings.
-	Set 'Mark devices with no compliance policy assigned as' to Not compliant (the secure option).
-	Set the compliance status validity period (default is 30 days).
2. Create a compliance policy per platform
-	Go to Devices > Compliance > Create policy and choose Windows, iOS, Android, or macOS.
-	Windows typical rules: BitLocker on, Secure Boot on, minimum OS version, Defender active, firewall on, and a maximum device threat level (Defender for Endpoint).
-	iOS and Android typical rules: passcode required, encryption, no jailbreak or root, minimum OS version.
3. Add actions for noncompliance
Action	Suggested timing
Mark device noncompliant	Day 0 (default)
Send email to end user	Day 1 to 3
Send push notification	Optional, day 1 to 3
Retire the noncompliant device	Only after a long grace period (for example 30 days)
The grace period lets users fix the problem before access is cut.
4. Assign the policy
-	Assign to a pilot group first, then to all users or devices.
-	Use assignment filters for exceptions
<img width="1025" height="350" alt="image" src="https://github.com/user-attachments/assets/c3b414a1-3305-499c-97a5-5c344222d268" />
<img width="908" height="290" alt="image" src="https://github.com/user-attachments/assets/1cc2ae3a-6d29-4ae6-8dd8-ad296781a9df" />
<img width="915" height="356" alt="image" src="https://github.com/user-attachments/assets/5a5668ca-5e97-4e24-9c16-980708f74372" />
<img width="890" height="284" alt="image" src="https://github.com/user-attachments/assets/3e63e7ab-2b6c-4515-9cc9-f672e3e327fa" />
<img width="871" height="128" alt="image" src="https://github.com/user-attachments/assets/7b994707-f031-40ea-a816-50dab0ec757d" />
<img width="865" height="301" alt="image" src="https://github.com/user-attachments/assets/62edd7c1-15bf-4a4a-a28d-9423564956ff" />
<img width="1025" height="315" alt="image" src="https://github.com/user-attachments/assets/940d5c94-47da-4f0f-a966-7463892e605e" />
<img width="1025" height="374" alt="image" src="https://github.com/user-attachments/assets/3fd35eda-883a-4dd6-b4d2-9f361d4f7a51" />
<img width="1025" height="319" alt="image" src="https://github.com/user-attachments/assets/33bbd8f2-42eb-4350-a93d-bcedbbfef2fd" />
<img width="1025" height="403" alt="image" src="https://github.com/user-attachments/assets/e155fde4-80a6-4e59-8179-de18c6186e9f" />
Devices evaluate and report
-	Devices check in shortly after enrollment, then roughly every 8 hours. Trigger Sync from the device page to force a check.
-	Review results under Devices > Compliance > Device compliance (per-policy view) and Reports.
Part 3: Quick Checklist and Best Practices
Done	Item
Licenses assigned and admin roles confirmed
	MDM user scope set in Entra ID; APNs / Google Play connected if needed
  	Enrollment method chosen and tested on a pilot device
  	Pilot and production groups created
  Configuration profiles and apps assigned
  Compliance policies per platform with noncompliance actions
  Conditional Access tested in Report-only, then enabled
  Always pilot first. A Conditional Access policy that requires compliance can lock users out if the compliance policy is wrong.
  Exclude emergency (break-glass) admin accounts from Conditional Access.
  Allow time for the first compliance evaluation before enforcing, so newly enrolled devices are not blocked.
