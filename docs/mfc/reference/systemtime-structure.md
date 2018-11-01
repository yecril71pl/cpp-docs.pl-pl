---
title: Struktura SYSTEMTIME
ms.date: 11/04/2016
f1_keywords:
- SYSTEMTIME
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
ms.openlocfilehash: b46482a9f4eb0165b72d74cb7d69e96e2a15e953
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559065"
---
# <a name="systemtime-structure"></a>Struktura SYSTEMTIME

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

