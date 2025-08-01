---
applicable: Skype for Business Server 2013, Skype for Business Server 2015, Skype for Business Server 2019
author: hirenshah1
external help file: Microsoft.Rtc.Management.dll-help.xml
Locale: en-US
manager: rogupta
Module Name: SkypeForBusiness
ms.author: hirshah
online version: https://learn.microsoft.com/powershell/module/skype/get-csplatformservicesettings
schema: 2.0.0
title: Get-CsPlatformServiceSettings
---

# Get-CsPlatformServiceSettings

## SYNOPSIS
Returns information about Skype for Business on Mac capabilities which have been enabled in your organization. This cmdlet was introduced in Skype for Business Server 2015 Cumulative Update 6 (December 2017).

## SYNTAX

### Identity (Default)
```
Get-CsPlatformServiceSettings [[-Identity] <XdsIdentity>] [-LocalStore] [<CommonParameters>]
```

### Filter
```
Get-CsPlatformServiceSettings [-Filter <String>] [-LocalStore] [<CommonParameters>]
```

## DESCRIPTION
Skype for Business Server 2015 Cumulative Update 6 introduces new features for Skype for Business on Mac users like support for E-911 calls, send files in peer-to-peer chats, block external access by policy and more.

The `Get-CsPlatformServiceSettings` cmdlet shows you which of these features are enabled.

## EXAMPLES

### EXAMPLE 1
```
PS C:\> Get-CsPlatformServiceSettings
```

This example shows you which of the Skype for Business on Mac features are enabled in your organization.

## PARAMETERS

### -Filter

> Applicable: Skype for Business Server 2015, Skype for Business Server 2019

Enables you to use wildcard characters in order to return one or more Platform Service Settings configurations.
For example, to return all of the Platform Service Settings configurations with the word Test in their names use this syntax:

-Filter "\*Test*"

```yaml
Type: String
Parameter Sets: Filter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Identity

> Applicable: Skype for Business Server 2015, Skype for Business Server 2019

Indicates the Identity of the Platform Service Settings to be returned.

```yaml
Type: XdsIdentity
Parameter Sets: Identity
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LocalStore

> Applicable: Skype for Business Server 2015, Skype for Business Server 2019

Retrieves the Platform Service Settings configuration data from the local replica of the Central Management store rather than from the Central Management store itself.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS
[New-CsPlatformServiceSettings](https://learn.microsoft.com/powershell/module/skype/new-csplatformservicesettings?view=skype-ps)

[Set-CsPlatformServiceSettings](https://learn.microsoft.com/powershell/module/skype/set-csplatformservicesettings?view=skype-ps)

[Remove-CsPlatformServiceSettings](https://learn.microsoft.com/powershell/module/skype/remove-csplatformservicesettings?view=skype-ps)
