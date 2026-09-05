# Active Directory Account Lockout Lab

**Scenario:** I configured and tested an account lockout policy in my Active Directory lab to simulate how an organization can protect domain accounts from repeated failed login attempts.

**1. Configure Account Lockout Policy**

I used Group Policy to configure an account lockout threshold of 3 failed login attempts.

**2. Apply and Verify the Policy**

I ran `gpupdate /force` to apply the updated Group Policy and verified that the account lockout settings were active.

**3. Test the Lockout Policy**

From my Windows 11 domain client, I intentionally entered an incorrect password multiple times to trigger the configured lockout policy.

**4. Verify the Account Lockout**

After reaching the failed login threshold, Windows prevented the domain account from logging in. I then verified the locked account in Active Directory.

**5. Restore Account Access**

I unlocked the account and confirmed that the user could regain access after the lockout was resolved.

**Tools used:** Active Directory Users and Computers • Group Policy Management • `gpupdate /force` • Windows 11 domain client

**Result:** Successfully configured, tested, and verified an Active Directory account lockout policy and practiced resolving a locked domain user account.
