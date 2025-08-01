---
applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019
author: jenstrier
external help file: Microsoft.Rtc.Management.dll-help.xml
Locale: en-US
manager: bulenteg
Module Name: SkypeForBusiness
ms.author: serdars
online version: https://learn.microsoft.com/powershell/module/skype/new-csvoicenormalizationrule
schema: 2.0.0
title: New-CsVoiceNormalizationRule
---

# New-CsVoiceNormalizationRule

## SYNOPSIS
Creates a new voice normalization rule.

Voice normalization rules are used to convert a telephone dialing requirement (for example, dialing 9 to access an outside line) to the E.164 phone number format used by
Skype for Business Server or Microsoft Teams.

This cmdlet was introduced in Lync Server 2010.


## SYNTAX

### Identity (Default)
```
New-CsVoiceNormalizationRule [-Tenant <Guid>] [-Description <String>] [-Pattern <String>]
 [-Translation <String>] [-IsInternalExtension <Boolean>] [-Priority <Int32>] [-Identity] <XdsIdentity>
 [-InMemory] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ParentAndRelativeKey
```
New-CsVoiceNormalizationRule [-Tenant <Guid>] -Parent <String> -Name <String> [-Description <String>]
 [-Pattern <String>] [-Translation <String>] [-IsInternalExtension <Boolean>] [-Priority <Int32>] [-InMemory]
 [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
This cmdlet creates a named voice normalization rule.
These rules are a required part of phone authorization and call routing.
They define the requirements for converting (or translating) numbers from an internal format to a standard (E.164) format.
An understanding of regular expressions is helpful in order to define number patterns that will be translated.

For Lync or Skype for Business Server, rules that are created by using this cmdlet are part of the dial plan and in addition to being accessible through the
The `Get-CsVoiceNormalizationRule` cmdlet can also be accessed through the NormalizationRules property returned by a call to the `Get-CsDialPlan` cmdlet.
You cannot create a normalization rule unless a dial plan with an Identity matching the scope specified in the normalization rule Identity already exists.
For example, you can't create a normalization rule with the Identity site:Redmond/RedmondNormalizationRule unless a dial plan for site:Redmond already exists.

For Microsoft Teams, rules that are created by using this cmdlet can only be created with the InMemory switch and should be added to a tenant dial plan using
the `New-CsTenantDialPlan` or `Set-CsTenantDialPlan` cmdlets.


## EXAMPLES

### Example 1
```
New-CsVoiceNormalizationRule -Identity "site:Redmond/Prefix Redmond"
```

This example creates a new voice normalization rule for site Redmond named Prefix Redmond.
Because no other parameters are specified, the rule is created with the default values.
Notice that the value passed to the Identity parameter is in double quotes; this is because the name of the rule (Prefix Redmond) contains a space.
If the rule name does not contain a space you don't need to enclose the Identity in double quotes.

Keep in mind that a dial plan for the Redmond site must exist for this command to succeed.
You can create a new dial plan by calling the `New-CsDialPlan` cmdlet.


### Example 2
```
New-CsVoiceNormalizationRule -Parent SeattleUser -Name SeattleFourDigit -Description "Dialing with internal four-digit extension" -Pattern '^(\d{4})$' -Translation '+1206555$1'
```

This example creates a new voice normalization rule named SeattleFourDigit that applies to the per-user dial plan with the Identity SeattleUser.
(Note: Rather than specifying a Parent and a Name, we could have instead created this same rule by specifying -Identity SeattleUser/SeattleFourDigit.) We've included a Description explaining that this rule is for translating numbers dialed internally with only a 4-digit extension.
In addition, Pattern and Translation values have been specified.
These values translate a four-digit number (specified by the regular expression in the Pattern) to the same four-digit number, but prefixed by the Translation value (+1206555).
For example, if the extension 1234 was entered, this rule would translate that extension to the number +12065551234.

Note the single quotes around the Pattern and Translation values.
Single quotes are required for these values; double quotes (or no quotes) will not work in this instance.

As in Example 1, a dial plan with the given scope must exist.
In this case, that means a dial plan with the Identity SeattleUser must already exist.

### Example 3
```
$nr1=New-CsVoiceNormalizationRule -Identity dp1/nr1 -Description "Dialing with internal four-digit extension" -Pattern '^(\d{4})$' -Translation '+1206555$1' -InMemory
New-CsTenantDialPlan -Identity DP1 -NormalizationRules @{Add=$nr1}
```

This example creates a new in-memory voice normalization rule and then adds it to a new tenant dial plan DP1 to be used for Microsoft Teams users.

## PARAMETERS

### -Description

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

A friendly description of the normalization rule.

Maximum string length: 512 characters.

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

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

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

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

A unique identifier for the rule.
The Identity specified must include the scope followed by a slash and then the name; for example: site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name.
The name portion will automatically be stored in the Name property.
You cannot specify values for Identity and Name in the same command.

For Lync and Skype for Business Server, voice normalization rules can be created at the following scopes: global, site, service (Registrar and PSTNGateway only) and per user.
A dial plan with an Identity matching the scope of the normalization rule must already exist before a new rule can be created.
(To retrieve a list of dial plans, call the `Get-CsDialPlan` cmdlet.)

For Microsoft Teams, voice normalization rules can be created at the following scopes: global and tag.

The Identity parameter is required unless the Parent parameter is specified.
You cannot include the Identity parameter and the Parent parameter in the same command.


```yaml
Type: XdsIdentity
Parameter Sets: Identity
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InMemory

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

Creates an object reference without actually committing the object as a permanent change.

For Lync or Skype for Business Server, if you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the
object reference and then commit those changes by calling this cmdlet's matching Set-\<cmdlet\>.

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

### -IsInternalExtension

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

If True, the result of applying this rule will be a number internal to the organization.
If False, applying the rule results in an external number.
This value is ignored if the value of the OptimizeDeviceDialing property of the associated dial plan/tenant dial plan is set to False.

Default: False

```yaml
Type: Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

The name of the rule.
This parameter is required if a value has been specified for the Parent parameter.
If no value has been specified for the Parent parameter, Name defaults to the name specified in the Identity parameter.
For example, if a rule is created with the Identity site:Redmond/RedmondRule, the Name will default to RedmondRule.
The Name parameter and the Identity parameter cannot be used in the same command.

```yaml
Type: String
Parameter Sets: ParentAndRelativeKey
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Parent

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

The scope at which the new normalization rule will be created.
This value must be global; site:\<sitename\>, where \<sitename\> is the name of the Skype for Business Server site; PSTN gateway or Registrar service, such as
PSTNGateway:redmond.litwareinc.com; or a string designating a per user rule.
A dial plan with the specified scope must already exist or the command will fail.

The Parent parameter is required unless the Identity parameter is specified.
You cannot include the Identity parameter and the Parent parameter in the same command.
If you include the Parent parameter, the Name parameter is also required.

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

### -Pattern

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

A regular expression that the dialed number must match in order for this rule to be applied.

Default: ^(\d{11})$ (The default represents any set of numbers up to 11 digits.)

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

### -Priority

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

The order in which rules are applied.
A phone number might match more than one rule.
This parameter sets the order in which the rules are tested against the number.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tenant

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019

For internal Microsoft usage.

```yaml
Type: Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Translation

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

The regular expression pattern that will be applied to the number to convert it to E.164 format.

Default: +$1 (The default prefixes the number with a plus sign \[+\].)

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

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

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

> Applicable: Lync Server 2010, Lync Server 2013, Skype for Business Server 2015, Skype for Business Server 2019, Microsoft Teams

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

### None

## OUTPUTS

### Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule
This cmdlet creates an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule.

## NOTES

## RELATED LINKS

[Remove-CsVoiceNormalizationRule](Remove-CsVoiceNormalizationRule.md)

[Set-CsVoiceNormalizationRule](Set-CsVoiceNormalizationRule.md)

[Get-CsVoiceNormalizationRule](Get-CsVoiceNormalizationRule.md)

[Test-CsVoiceNormalizationRule](Test-CsVoiceNormalizationRule.md)

[New-CsDialPlan](New-CsDialPlan.md)

[Get-CsDialPlan](Get-CsDialPlan.md)

