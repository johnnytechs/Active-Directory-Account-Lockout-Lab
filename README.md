# Active Directory Account Lockout Lab

**Scenario:** I configured and tested an account lockout policy in my Active Directory lab to simulate a common Help Desk issue where a domain user becomes locked out after repeated failed login attempts. I then investigated the locked account in Active Directory, restored access, and verified the user could successfully log in again.

## 1. Configure the Account Lockout Policy

I configured the Default Domain Policy to lock domain accounts after **3 failed login attempts**, with a **30-minute lockout duration** and a **30-minute lockout observation window**.

<img width="1040" height="992" alt="01-account-lockout-policy" src="https://github.com/user-attachments/assets/c9b3cb21-02a9-435e-a975-d394db9b23d3" />


## 2. Apply the Group Policy

On the Windows 11 domain client, I ran `gpupdate /force` to refresh Computer and User Group Policy after configuring the account lockout settings.

<img width="989" height="853" alt="02-gpupdate-force png" src="https://github.com/user-attachments/assets/b1fa06e1-162f-4c10-85b2-919070e5b369" />


## 3. Verify the Account Lockout Policy

I ran `net accounts` on the Windows 11 client to verify the effective policy. The results confirmed a lockout threshold of **3 attempts**, a **30-minute lockout duration**, and a **30-minute observation window**.

<img width="2142" height="734" alt="03-lockout-policy-verification" src="https://github.com/user-attachments/assets/c538f609-656e-46ab-adb3-051f75e59fa5" />


## 4. Trigger the Account Lockout

I intentionally entered an incorrect password multiple times for the Marc domain account. After reaching the configured threshold, Windows prevented the account from logging in and displayed an account lockout message.

<img width="1448" height="1086" alt="04-account-locked png" src="https://github.com/user-attachments/assets/c4a3e62a-e9f1-4c12-bbc5-99c1da285869" />


## 5. Investigate and Unlock the Account

I opened Marc's account properties in Active Directory Users and Computers and confirmed that the account was locked out. I used the **Unlock account** option to restore access.

<img width="1082" height="992" alt="05-ad-account-locked" src="https://github.com/user-attachments/assets/df57341f-30f7-47f4-830d-30876c7e0129" />


## 6. Verify Account Access Is Restored

After unlocking the account, I successfully logged back into the Windows 11 domain client as Marc and used `whoami` to verify the authenticated domain account.

<img width="1191" height="896" alt="06-account-access-restored png" src="https://github.com/user-attachments/assets/7e1e34b8-eff1-49d1-a60b-90505c624dde" />


**Tools used:** Active Directory Users and Computers • Group Policy Management Editor • `gpupdate /force` • `net accounts` • `whoami` • Windows Server • Windows 11

**Result:** Successfully configured and verified an Active Directory account lockout policy, reproduced a domain account lockout, identified the locked account in Active Directory, restored access, and verified successful authentication.

## What I Learned

I learned how Active Directory account lockout policies protect domain accounts from repeated failed login attempts and how to verify that the configured policy is actually being enforced.

I also practiced the Help Desk troubleshooting process of identifying a locked domain account, restoring the user's access in Active Directory, and verifying that the user could successfully authenticate afterward.

**Configure → Apply → Verify → Reproduce → Investigate → Resolve → Verify**
