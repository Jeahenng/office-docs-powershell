---
applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019
author: hirenshah1
external help file: Microsoft.Rtc.Management.dll-help.xml
Locale: en-US
manager: rogupta
Module Name: SkypeForBusiness
ms.author: hirshah
online version: https://learn.microsoft.com/powershell/module/skype/set-csvoicetestconfiguration
schema: 2.0.0
title: Set-CsVoiceTestConfiguration
---

# Set-CsVoiceTestConfiguration

## SYNOPSIS
Modifies a test scenario you can use to test phone numbers against specified routes and rules.
This cmdlet was introduced in Lync Server 2010.


## SYNTAX

### Identity
```
Set-CsVoiceTestConfiguration [[-Identity] <XdsGlobalRelativeIdentity>] [-DialedNumber <String>]
 [-ExpectedRoute <String>] [-ExpectedTranslatedNumber <String>] [-ExpectedUsage <String>]
 [-TargetDialplan <String>] [-TargetVoicePolicy <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Instance
```
Set-CsVoiceTestConfiguration [-Instance <PSObject>] [-DialedNumber <String>] [-ExpectedRoute <String>]
 [-ExpectedTranslatedNumber <String>] [-ExpectedUsage <String>] [-TargetDialplan <String>]
 [-TargetVoicePolicy <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Before implementing voice routes and voice policies, it's a good idea to test them out on various phone numbers to ensure the results are what you're expecting.
You can do this by modifying test scenarios with this cmdlet.

The `Set-CsVoiceTestConfiguration` cmdlet modifies the voice route, usage, dial plan and voice policy against which to test a specified phone number.
All of this information can be defined and retrieved using other cmdlets, as specified in the parameter descriptions for this topic.

The configurations modified with this cmdlet are tested using the `Test-CsVoiceTestConfiguration` cmdlet.


## EXAMPLES

### Example 1
```
Set-CsVoiceTestConfiguration -Identity TestConfig1 -DialedNumber 14255551212
```

This example sets the dialed number of the voice test configuration for TestConfig1 to 14255551212.
This is the number that will be checked against the voice policy and route to ensure normalization occurs as expected, as well as to ensure the correct routes and dial plans are being applied.


### Example 2
```
Set-CsVoiceTestConfiguration -Identity TestConfig1 -TargetDialPlan site:Redmond1 -ExpectedTranslatedNumber "+912065551212"
```

This example modifies settings for the voice test configuration TestConfig1.
The command sets the TargetDialPlan to the dial plan for site:Redmond1.
Because a change in dial plan could mean a change in normalization rules, the ExpectedTranslationNumber has also been changed to reflect what is expected from the normalization rules for that dial plan.


## PARAMETERS

### -DialedNumber

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

The phone number you want to use to test the policies, usages, and so on.

Must be 512 characters or fewer.

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

### -ExpectedRoute

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

The name of the voice route expected to be used during the configuration test.
If a different route is used, based on the target dial plan and voice policy, the test will fail.
You can retrieve available voice routes by calling the `Get-CsVoiceRoute` cmdlet.

Must be 256 characters or fewer.

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

### -ExpectedTranslatedNumber

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

The phone number in the format you expect to see it in after translation.
This is the value of the DialedNumber parameter after normalization.
If you run the `Test-CsVoiceTestConfiguration` cmdlet and the DialedNumber does not result in the value in ExpectedTranslatedNumber, the test will report as Fail.

Must be 512 characters or fewer.


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

### -ExpectedUsage

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

The name of the PSTN usage expected to be used during the configuration test.
If a different PSTN usage is used, based on the target dial plan and voice policy, the test will fail.
You can retrieve available usages by calling the `Get-CsPstnUsage` cmdlet.

Must be 256 characters or fewer.


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

### -Force

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

Suppresses any confirmation prompts that would otherwise be displayed before making changes.

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

### -Identity

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

A string uniquely identifying the test scenario you want to modify.

The value of this parameter does not include scope because this object can be created only at the global scope.
Therefore only a name is required.

```yaml
Type: XdsGlobalRelativeIdentity
Parameter Sets: Identity
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Instance

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

An object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration that contains an existing voice test configuration with the changes you'd like to make to that configuration.
An object of this type can be retrieved by calling the `Get-CsVoiceTestConfiguration` cmdlet.

```yaml
Type: PSObject
Parameter Sets: Instance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -TargetDialplan

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

The Identity of the dial plan to be used for this test.
Dial plans can be retrieved by calling the `Get-CsDialPlan` cmdlet.

Must be 40 characters or fewer.

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

### -TargetVoicePolicy

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

The Identity of the voice policy against which to run this test.
Voice policies can be retrieved by calling the `Get-CsVoicePolicy` cmdlet.

Must be 40 characters or fewer.


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

### -Confirm

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

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

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration

Accepts pipelined input of voice test configuration objects.

## OUTPUTS

### Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration
This cmdlet returns an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration.

## NOTES

## RELATED LINKS

[New-CsVoiceTestConfiguration](New-CsVoiceTestConfiguration.md)

[Remove-CsVoiceTestConfiguration](Remove-CsVoiceTestConfiguration.md)

[Get-CsVoiceTestConfiguration](Get-CsVoiceTestConfiguration.md)

[Test-CsVoiceTestConfiguration](Test-CsVoiceTestConfiguration.md)

[Get-CsVoiceRoute](Get-CsVoiceRoute.md)

[Get-CsPstnUsage](Get-CsPstnUsage.md)

[Get-CsDialPlan](Get-CsDialPlan.md)

[Get-CsVoicePolicy](Get-CsVoicePolicy.md)
