---
applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019
author: hirenshah1
external help file: Microsoft.Rtc.Management.dll-help.xml
Locale: en-US
manager: rogupta
Module Name: SkypeForBusiness
ms.author: hirshah
online version: https://learn.microsoft.com/powershell/module/skype/get-csvoiceconfiguration
schema: 2.0.0
title: Get-CsVoiceConfiguration
---

# Get-CsVoiceConfiguration

## SYNOPSIS
Retrieves the voice configuration object, which contains a full list of all voice test configurations defined for the Skype for Business Server deployment.
This cmdlet was introduced in Lync Server 2010.



## SYNTAX

### Identity
```
Get-CsVoiceConfiguration [[-Identity] <XdsIdentity>] [-LocalStore] [<CommonParameters>]
```

### Filter
```
Get-CsVoiceConfiguration [-Filter <String>] [-LocalStore] [<CommonParameters>]
```

## DESCRIPTION
Voice test configurations are used to test a phone number against a specific voice policy, route, and dial plan.
This cmdlet is used to retrieve the global instance that holds a list of all voice test configurations defined within the Skype for Business Server 2015 deployment.
To retrieve individual voice test configurations or to retrieve them as individual objects rather than as a list, use the Get-CsVoiceTestConfiguration cmdlet.



## EXAMPLES

### Example 1
```
Get-CsVoiceConfiguration
```

This example retrieves the voice configuration.
To retrieve the voice test configurations, use the Get-CsVoiceTestConfiguration cmdlet.

## PARAMETERS

### -Filter

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

There can only be one instance of this object, so this parameter does nothing.

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

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

The scope of the voice configuration to retrieve.
The only possible value is Global.

```yaml
Type: XdsIdentity
Parameter Sets: Identity
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LocalStore

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

Retrieves the voice configuration from the local replica of the Central Management store, rather than the Central Management store itself.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration
This cmdlet returns an instance of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration object.

## NOTES

## RELATED LINKS

[Remove-CsVoiceConfiguration](Remove-CsVoiceConfiguration.md)

[Set-CsVoiceConfiguration](Set-CsVoiceConfiguration.md)

[Get-CsVoiceTestConfiguration](Get-CsVoiceTestConfiguration.md)
