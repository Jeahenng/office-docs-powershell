---
applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019
author: hirenshah1
external help file: Microsoft.Rtc.Management.dll-help.xml
Locale: en-US
manager: rogupta
Module Name: SkypeForBusiness
ms.author: hirshah
online version: https://learn.microsoft.com/powershell/module/skype/move-csmeetingroom
schema: 2.0.0
title: Move-CsMeetingRoom
---

# Move-CsMeetingRoom

## SYNOPSIS
Moves a Skype for Business Server 2015 meeting room object from one Registrar pool to another, or to Skype for Business Online.
A meeting room is a conferencing device designed to address video conferencing and collaboration scenarios in small conference rooms.
This cmdlet was introduced in Lync Server 2013.

## SYNTAX

### Identity (Default)
```
Move-CsMeetingRoom [-HostedMigrationOverrideUrl <String>] [-Credential <PSCredential>] [-Target] <Fqdn>
 [-Report <String>] [-Force] [-IgnoreBackendStoreException] [-ProxyPool <Fqdn>] [-DomainController <Fqdn>]
 [-Identity] <UserIdParameter> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Users
```
Move-CsMeetingRoom [-HostedMigrationOverrideUrl <String>] [-Credential <PSCredential>] [-Target] <Fqdn>
 -UserList <String> [-Report <String>] [-Force] [-IgnoreBackendStoreException] [-ProxyPool <Fqdn>]
 [-DomainController <Fqdn>] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
In Skype for Business Server 2015, meeting rooms are self-contained computer appliances that are installed in conference rooms and supply advanced meeting capabilities such as:

* One touch meeting join experience
* Multi-view video gallery
* Touch-enabled white-boarding on the front of room screen
* Calendar integration to provide access to scheduled meetings
* Content sharing and switching

In order to manage these new endpoint devices you must, among other things, create and enable an Exchange resource mailbox account for the device, then enable that resource account for Skype for Business Server 2015.
Note that, for Skype for Business Server 2015, there are no cmdlets for creating or removing meeting rooms.
Instead, you use the Enable-CsMeetingRoom cmdlet to enable meeting rooms and the Disable-CsMeetingRoom cmdlet to disable meeting rooms.
The resource account must already exist in order for you to enable the meeting room, and disabling a meeting room only removes that room from your collection of meeting rooms; it does not delete the resource mailbox account.

Skype for Business Server Control Panel: The functions carried out by the Move-CsMeetingRoom cmdlet are not available in the Skype for Business Server Control Panel.



## EXAMPLES

### Example 1
```
Move-CsMeetingRoom -Target "atl-cs-001.litwareinc.com" -Identity "Room 14"
```

The command shown in Example 1 moves the meeting room with the display name "Room 14" to the pool atl-cs-001.litwareinc.com.

### Example 2
```
Get-CsMeetingRoom | Move-CsMeetingRoom -Target "atl-cs-001.litwareinc.com"
```

Example 2 moves all the meeting rooms in the organization to the pool atl-cs-001.litwareinc.com.
To do this, the command first calls the Get-CsMeetingRoom cmdlet without any parameters; that returns a collection of all the meeting rooms configured for use in the organization.
That collection is then piped to the Move-CsMeetingRoom cmdlet, which moves each meeting room in the collection to the new pool.

### Example 3
```
Move-CsMeetingRoom -Identity "Room 15" -HostedMigrationOverrideUrl "https://admin2a.online.lync.com/HostedMigration/hostedmigrationservice.svc" -Target "sipfed.online.lync.com" -Credential $credential
```

The command shown in Example 3 moves the meeting room with the display name "Room 15" to Skype for Business Online.

## PARAMETERS

### -Credential
Enables you to run the Move-CsMeetingRoom cmdlet under alternate credentials.
This might be required if the account you used to log on to Windows does not have the necessary privileges required to work with user objects.

To use the Credential parameter you must first create a PSCredential object using the Get-Credential cmdlet.
For details, see the Get-Credential cmdlet help topic.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainController

> Applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

Enables you to connect to the specified domain controller in order to move a meeting room.
To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-dc-001) or its fully qualified domain name (FQDN) (for example, atl-dc-001.litwareinc.com).

```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

> Applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

When present, instructs the Move-CsMeetingRoom cmdlet to ignore all errors that might occur when carrying out the move operation.
As a general rule, you should avoid using the Force parameter unless absolutely necessary.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostedMigrationOverrideUrl
URL for the hosted migration service used when moving a user to Lync Online.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Identity

> Applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

Indicates the Identity of the meeting room to be moved.
Meeting rooms can be specified using one of four formats: 1) the room's SIP address; 2) the room's user principal name (UPN); 3) the room's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the room's Active Directory display name (for example, Main Conference Room).
User Identities can also be referenced by using the room's Active Directory distinguished name.

```yaml
Type: UserIdParameter
Parameter Sets: (All), Identity
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -IgnoreBackendStoreException

> Applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

When present, instructs the computer to ignore any errors that might occur with the backend database and attempt to the move meeting room despite those errors.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

> Applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

Enables you to pass a meeting room object through the pipeline that represents the meeting room being moved.
By default, the Move-CsMeetingRoom cmdlet does not pass objects through the pipeline.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyPool

> Applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

This parameter is not used with the on-premises version of Skype for Business Online.

```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Report

> Applicable: Skype for Business Server 2015, Skype for Business Server 2019

Specifies the file path for the log file created when the cmdlet runs.
For example: -Report "C:\Logs\S1_FailOverLog.html".
If this file already exists, it will be overwritten.
By default, reports are written to the "AppData\Local\Temp" folder in your user profile.

```yaml
Type: String
Parameter Sets: Identity, Users
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Target

> Applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

The FQDN (for example, atl-cs-001.litwareinc.com) of the Registrar pool where the meeting room should be moved.

```yaml
Type: Fqdn
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserList

> Applicable: Skype for Business Server 2015, Skype for Business Server 2019

PARAMVALUE: String

```yaml
Type: String
Parameter Sets: Users
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

> Applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

Prompts you for confirmation before executing the command.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

> Applicable: Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

Describes what would happen if you executed the command without actually executing the command.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: `-Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).`

## INPUTS

### Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom
The Moves-CsMeetingRoom cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom object.

## OUTPUTS

### None

## NOTES

## RELATED LINKS

[Disable-CsMeetingRoom](Disable-CsMeetingRoom.md)

[Enable-CsMeetingRoom](Enable-CsMeetingRoom.md)

[Get-CsMeetingRoom](Get-CsMeetingRoom.md)

[Set-CsMeetingRoom](Set-CsMeetingRoom.md)
