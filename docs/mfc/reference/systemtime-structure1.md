---
title: Struktura1 SYSTEMTIME | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79c7cec92550ad51b53242b44b3aee334be21f3f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397211"
---
# <a name="systemtime-structure1"></a>Struktura1 SYSTEMTIME

`SYSTEMTIME` Struktury reprezentuje datę i godzinę przy użyciu poszczególnych elementów członkowskich dla miesiąca, dnia, roku, dzień tygodnia, godziny, minuty, sekundy i milisekundy.

## <a name="syntax"></a>Składnia

```
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME;
```

#### <a name="parameters"></a>Parametry

*wYear*<br/>
Bieżący rok.

*wartość zero*<br/>
Bieżący miesiąc; Styczeń to 1.

*Może*<br/>
Bieżący dzień tygodnia; Niedziela to 0, poniedziałek to 1 i tak dalej.

*tej notacji*<br/>
Bieżący dzień miesiąca.

*wDayOfWeek*<br/>
Bieżąca godzina.

*Dnia*<br/>
Bieżąca minuta.

*Poprzez*<br/>
Bieżąca sekunda.

*wMilliseconds*<br/>
Bieżąca Milisekunda.

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** winbase.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

