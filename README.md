Full details and how signing works can be found here:
https://www.tenaka.net/post/creating-and-enforcing-a-signed-wdac-policy-with-powershell

Windows Defender Application Control (WDAC) was previously known as DeviceGuard, now it's named App Control for Business. It is one of the strongest application-control technologies available in Windows. From this point forward, it will be referred to as WDAC.



Creating a basic WDAC policy is relatively straightforward. Creating a signed WDAC policy that boots correctly, survives administrative tampering and can still be safely updated is considerably more challenging. I've lost count of the Windows systems that failed to survive signing and ended with a BSoD.



The problem with devising a signed policy is that the information is spread across separate pages covering policy creation, rule options, certificate signing, deployment, Secure Boot and policy removal. Turning those individual components into a reliable end-to-end process required a fair amount of effort and trial and error, heavy on the error.



This article describes the lab process used to:





Scan a Windows 11 reference system.



Create and test an audit policy.



Convert it to unsigned enforcement.



Add an authorised policy update signer.



Sign the policy using SignTool.



Deploy it to Windows and the EFI system partition.



Confirm that removing the Windows policy file does not simply disable enforcement.

Important: This is a lab proof of concept. The scripts and procedures described here are not currently suitable for an enterprise production deployment.
