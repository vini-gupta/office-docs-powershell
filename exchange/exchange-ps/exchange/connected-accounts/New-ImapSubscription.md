---
external help file: Microsoft.Exchange.RemoteConnections-Help.xml
applicable: Exchange Online
title: New-ImapSubscription
schema: 2.0.0
author: chrisda
ms.author: chrisda
ms.reviewer:
monikerRange: "exchonline-ps"
---

# New-ImapSubscription

## SYNOPSIS
This cmdlet is available only in the cloud-based service.

The New-ImapSubscription cmdlet allows a user to create IMAP subscriptions in their own cloud-based mailbox. An administrator can't use this cmdlet to create subscriptions in another user's mailbox.

For information about the parameter sets in the Syntax section below, see [Exchange cmdlet syntax](https://docs.microsoft.com/powershell/exchange/exchange-server/exchange-cmdlet-syntax).

## SYNTAX

```
New-ImapSubscription [-Name] <String> -EmailAddress <SmtpAddress> -IncomingPassword <SecureString>
 -IncomingServer <Fqdn> -IncomingUserName <String> [-Confirm] [-DisplayName <String>] [-Force]
 [-IncomingAuth <Basic | Ntlm>] [-IncomingPort <Int32>] [-IncomingSecurity <None | Ssl | Tls>]
 [-Mailbox <MailboxIdParameter>] [-WhatIf] [<CommonParameters>]
```

## DESCRIPTION
The New-ImapSubscription cmdlet creates a connection between a user's cloud-based mailbox and a remote IMAP mailbox. The cloud-based mailbox periodically polls the IMAP mailbox for new messages.

You need to be assigned permissions before you can run this cmdlet. Although this topic lists all parameters for the cmdlet, you may not have access to some parameters if they're not included in the permissions assigned to you. To find the permissions required to run any cmdlet or parameter in your organization, see [Find the permissions required to run any Exchange cmdlet](https://docs.microsoft.com/powershell/exchange/exchange-server/find-exchange-cmdlet-permissions).

## EXAMPLES

### Example 1
```powershell
New-ImapSubscription -Name "Contoso IMAP" -EmailAddress kakers@contoso.com -IncomingUserName kakers -IncomingPassword (ConvertTo-SecureString -String 'Pa$$word1' -AsPlainText -Force) -IncomingServer imap.contoso.com -IncomingSecurity Ssl -IncomingPort 993
```

This example creates the IMAP subscription Contoso IMAP in the mailbox of the user Kim Akers. The remote IMAP mailbox has the following details:

- Email address: kakers@contoso.com

- User name: kakers

- Password: Pa$$word1

- IMAP server: imap.contoso.com

- Authentication method: SSL

- TCP port: 993

## PARAMETERS

### -EmailAddress
The EmailAddress parameter specifies the email address of the IMAP mailbox.

```yaml
Type: SmtpAddress
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncomingPassword
The IncomingPassword parameter specifies the password used to sign in to the IMAP mailbox.

This parameter uses the syntax `(ConvertTo-SecureString -String '<password>' -AsPlainText -Force)`. Or, before you run this command, store the password as a variable (for example, `$password = Read-Host "Enter password" -AsSecureString`), and then use the variable name (`$password`) for this parameter.

```yaml
Type: SecureString
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncomingServer
The IncomingServer parameter specifies the fully qualified domain name (FQDN) of the IMAP server, for example, incoming.contoso.com.

```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncomingUserName
The IncomingUserName parameter specifies the username used to sign in to the IMAP mailbox.

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
The Name parameter specifies the name of the IMAP subscription. The name of the subscription doesn't have to be globally unique. The name must be unique compared to other subscriptions that exist in the same mailbox.

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
The Confirm switch specifies whether to show or hide the confirmation prompt. How this switch affects the cmdlet depends on if the cmdlet requires confirmation before proceeding.

- Destructive cmdlets (for example, Remove-\* cmdlets) have a built-in pause that forces you to acknowledge the command before proceeding. For these cmdlets, you can skip the confirmation prompt by using this exact syntax: -Confirm:$false.

- Most other cmdlets (for example, New-\* and Set-\* cmdlets) don't have a built-in pause. For these cmdlets, specifying the Confirm switch without a value introduces a pause that forces you acknowledge the command before proceeding.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName
The DisplayName parameter specifies the friendly name of the IMAP subscription. If you don't specify a value for the DisplayName parameter, the value of the EmailAddress parameter is used.

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
The Force parameter instructs the command to create the subscription even if those settings can't be verified by the remote IMAP server.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncomingAuth
The IncomingAuth parameter sets the authentication method used by IMAP clients to access the IMAP server. Valid values are Basic or Ntlm. If you don't specify a value for the IncomingAuth parameter, the value Basic is used.

```yaml
Type: Basic | Ntlm
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncomingPort
The IncomingPort parameter specifies the TCP port number used by IMAP clients to connect to the IMAP server. Typical values are 143 for unencrypted connections and 993 for encrypted connections. By default, the value of the IncomingPort parameter is set to 143 if you don't set the IncomingSecurity parameter to Ssl or Tls. If you set the IncomingSecurity parameter to Ssl or Tls, the value of the IncomingPort parameter is set to 993. You can override the default values by specifying an integer for the IncomingPort parameter.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncomingSecurity
The IncomingSecurity parameter specifies the encryption method used by IMAP clients to connect to the IMAP server. Valid values are None, Ssl, or Tls. If you don't specify a value for the IncomingSecurity parameter, the value None is used.

```yaml
Type: None | Ssl | Tls
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Mailbox
The Mailbox parameter specifies the cloud-based mailbox that will contain the IMAP subscription. You can use any value that uniquely identifies the mailbox. For example:

- Name

- Alias

- Distinguished name (DN)

- Canonical DN

- \<domain name\>\\\<account name\>

- Email address

- GUID

- LegacyExchangeDN

- SamAccountName

- User ID or user principal name (UPN)

```yaml
Type: MailboxIdParameter
Parameter Sets: (All)
Aliases:
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### -WhatIf
The WhatIf switch simulates the actions of the command. You can use this switch to view the changes that would occur without actually applying those changes. You don't need to specify a value with this switch.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi
Applicable: Exchange Online

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/p/?LinkID=113216).

## INPUTS

###  
To see the input types that this cmdlet accepts, see [Cmdlet Input and Output Types](https://go.microsoft.com/fwlink/p/?linkId=616387). If the Input Type field for a cmdlet is blank, the cmdlet doesn't accept input data.

## OUTPUTS

###  
To see the return types, which are also known as output types, that this cmdlet accepts, see [Cmdlet Input and Output Types](https://go.microsoft.com/fwlink/p/?linkId=616387). If the Output Type field is blank, the cmdlet doesn't return data.

## NOTES

## RELATED LINKS

[Online Version](https://technet.microsoft.com/library/cb002b53-c307-40a6-aca2-a7f29dc740d8.aspx)