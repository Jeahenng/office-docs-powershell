---
external help file: Microsoft.Rtc.Management.dll-Help.xml
online version: https://learn.microsoft.com/powershell/module/teams/New-CsMainlineAttendantQuestionAnswerFlow 
applicable: Microsoft Teams
title: New-CsMainlineAttendantQuestionAnswerFlow
author: tomkau
ms.author: tomkau
manager: bulenteg
ms.reviewer:
schema: 2.0.0
---

# New-CsMainlineAttendantQuestionAnswerFlow

## SYNOPSIS
Creates new Mainline Attendant question and answer (FAQ) flow

## SYNTAX

```
New-CsMainlineAttendantQuestionAnswerFlow -Name <String> -Description <String>  -ApiAuthenticationType <basic | api_key | bearer_token_static | bearer_token_dynamic> -KnowledgeBase <String> [-Tenant <Guid>] [<CommonParameters>]
```

## DESCRIPTION
The New-CsMainlineAttendantQuestionAnswerFlow cmdlet creates a question and answer connection that can be used with Mainline Attendant

> [!CAUTION]
> This cmdlet will only work for customers that are participating in the Voice Applications private preview for these features. General Availability for this functionality has not been determined at this time.

## EXAMPLES


## PARAMETERS

### -Name
The name of the question and answer flow

```yaml
Type: String
Parameter Sets: (All)
Aliases:
applicable: Microsoft Teams

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description
The description for the question and answer flow

```yaml
Type: String
Parameter Sets: (All)
Aliases:
applicable: Microsoft Teams

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

###  -ApiAuthenticationType
The method of authentication used by the API

PARAVALUES: basic | api_key | bearer_token_static | bearer_token_dynamic

```yaml
Type: String
Parameter Sets: (All)
Aliases:
applicable: Microsoft Teams

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

###  -KnowledgeBase
The knowledge base definition

The parameters used by the API

For an example, see [New-CsMainlineAttendantQuestionAnswerFlow -KnowledgeBase](./New-CsMainlineAttendantQuestionAnswerFlowKnowledgeBaseJSON.md)

```yaml
Type: String
Parameter Sets: (All)
Aliases:
applicable: Microsoft Teams

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### Microsoft.Rtc.Management.Hosted.CallQueue.Models.CallQueue

## NOTES

## RELATED LINKS

