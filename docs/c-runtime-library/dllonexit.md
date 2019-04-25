---
title: __dllonexit
ms.date: 11/04/2016
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
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
ms.openlocfilehash: a6c077ac010c0b5d94ba21ba823441ea6ac932b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290316"
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
|__dllonexit|onexit.c|

## <a name="see-also"></a>Zobacz także

[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
