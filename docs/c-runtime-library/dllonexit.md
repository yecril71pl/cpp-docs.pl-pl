---
title: __dllonexit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __dllonexit
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- __dllonexit
dev_langs:
- C++
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c2c04f623ba8cac2f3b967007079d41689d2346
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062868"
---
# <a name="dllonexit"></a>__dllonexit

Rejestruje procedury wywoływanej w momencie zakończenia.

## <a name="syntax"></a>Składnia

```
_onexit_t __dllonexit(   _onexit_t func,
   _PVFV **  pbegin,
   _PVFV **  pend
   )
```

#### <a name="parameters"></a>Parametry

*FUNC*<br/>
Wskaźnik na funkcję, która ma być wykonywane przy zamykaniu.

*pbegin*<br/>
Wskaźnik do zmiennej, która odłączyć punktów na początku listy funkcji, które można wykonać na.

*Oczekujący*<br/>
Wskaźnik do zmiennej, która odłączyć punktów na końcu listy funkcji, które można wykonać na.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wskaźnik do funkcji użytkownika. W przeciwnym razie **NULL** wskaźnika.

## <a name="remarks"></a>Uwagi

`__dllonexit` Funkcji jest odpowiednikiem [_onexit](../c-runtime-library/reference/onexit-onexit-m.md) działać z tą różnicą, że zmienne globalne, które korzystają z tej funkcji nie są widoczne dla tej procedury. Zamiast zmiennych globalnych, ta funkcja używa `pbegin` i `pend` parametrów.

`_onexit` i `atexit` funkcji w bibliotece DLL połączona z MSVCRT. LIB, musisz utrzymywać własne listy atexit/_onexit. Ta procedura jest proces roboczy, który jest wywoływana przez takie biblioteki dll.

`_PVFV` Typ jest zdefiniowany jako `typedef void (__cdecl *_PVFV)(void)`.

## <a name="requirements"></a>Wymagania

|Procedura|Wymaganego pliku|
|-------------|-------------------|
|__dllonexit|OnExit.c|

## <a name="see-also"></a>Zobacz też

[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)