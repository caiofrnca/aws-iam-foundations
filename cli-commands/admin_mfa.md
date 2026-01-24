## TASK 4 — Multi-Factor Authentication (MFA)

#### Objectives:
Enforce MFA for privileged IAM users to reduce the risk of account compromise caused by leaked or reused credentials (For this task, MFA is enforced only for privileged users (Admins)).

1 - Check existing MFA devices for admin user
```bash
aws iam list-mfa-devices --user-name admin-user
```

2 - create a virtual MFA device. (generates a QR code for an authenticator app.)
```bash
aws iam create-virtual-mfa-device --virtual-mfa-device-name admin-user-mfa --bootstrap-method QRCodePNG --outfile admin-user-mfa-qr.png
```

3 - Enable MFA (after scan with authenticator app (authy, google authenticator, etc))
```bash
$ACCOUNT_ID = aws sts get-caller-identity --query Account --output text
aws iam enable-mfa-device --user-name admin-user --serial-number arn:aws:iam::$ACCOUNT_ID:mfa/admin-user-mfa --authentication-code1 <CODE> --authentication-code2 <CODE>
```
Verify MFA is enable:
```bash
aws iam list-mfa-devices --user-name admin-user
```
