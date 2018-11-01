---
title: _initterm, _initterm_e
ms.date: 11/04/2016
apiname:
- _initterm_e
- _initterm
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _initterm_e
- initterm
- _initterm
- initterm_e
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
ms.openlocfilehash: 65963e95507d4d6444ebcc9038b5b8cf797f9feb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620717"
---
# <a name="initterm-initterme"></a>_initterm, _initterm_e

Metod wewnętrznych, zapoznaj się z tabelą wskaźników funkcji, które ich inicjowania.

Pierwszy wskaźnik znajdują się już w tabeli, a drugi wskaźnik jest lokalizacja końcowa.

## <a name="syntax"></a>Składnia

```C
void __cdecl _initterm(
   PVFV *,
   PVFV *
);

int __cdecl _initterm_e(
   PVFV *,
   PVFV *
);
```

## <a name="return-value"></a>Wartość zwracana

Kod błędu różny od zera, jeśli inicjowanie zakończy się niepowodzeniem i zgłasza błąd; 0, jeśli żaden błąd nie wystąpi.

## <a name="remarks"></a>Uwagi

Te metody są wewnętrznie wywołana tylko podczas inicjowania programu w języku C++. Nie należy wywoływać tych metod w programie.

Gdy te metody zapoznaj się z tabelą funkcji wpisów, pomijają **NULL** wpisów i kontynuować.

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
