---
title: Struktura FILETIME
ms.date: 11/04/2016
f1_keywords:
- FILETIME
helpviewer_keywords:
- FILETIME structure [MFC]
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
ms.openlocfilehash: f70792b83637018e707b6ee48d1b169f28d46d71
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514936"
---
# <a name="filetime-structure"></a>Struktura FILETIME

`FILETIME` Struktura jest 64-bitowych reprezentującą liczbę 100-nanosekundowych interwałów, od 1 stycznia 1601.

## <a name="syntax"></a>Składnia

```
typedef struct _FILETIME {
    DWORD dwLowDateTime;   /* low 32 bits */
    DWORD dwHighDateTime;  /* high 32 bits */
} FILETIME, *PFILETIME, *LPFILETIME;
```

#### <a name="parameters"></a>Parametry

*dwLowDateTime*<br/>
Określa niskim 32 bity czas pliku.

*dwHighDateTime*<br/>
Określa ogólne 32 bity czas pliku.

## <a name="requirements"></a>Wymagania

**Nagłówek:** windef.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

